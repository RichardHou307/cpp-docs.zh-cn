---
title: 演练： 从用户界面线程中删除工作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d87fe1060756e46418411584fa6042533bbc1f2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385503"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>演练：从用户界面线程中移除工作

本文档演示如何使用并发运行时移动到工作线程的 Microsoft 基础类 (MFC) 应用程序中的用户界面 (UI) 线程执行的工作。 本文档还演示如何提高长的绘制操作的性能。

通过卸载阻塞操作从 UI 线程中移除工作，例如，绘图，到工作线程可以提高您的应用程序的响应能力。 本演练使用生成来演示较长的阻止操作 Mandelbrot 不规则图形的绘图例程。 生成的 Mandelbrot 不规则图形也是并行化的良好候选项，因为每个像素的计算是独立于其他所有计算。

## <a name="prerequisites"></a>系统必备

在开始本演练之前，请阅读以下主题：

- [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [消息传递函数](../../parallel/concrt/message-passing-functions.md)

- [并行算法](../../parallel/concrt/parallel-algorithms.md)

- [PPL 中的取消操作](cancellation-in-the-ppl.md)

我们还建议在开始本演练之前了解 MFC 应用程序开发和 GDI + 的基础知识。 有关 MFC 的详细信息，请参阅[MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)。 关于 GDI + 的详细信息，请参阅[GDI +](https://msdn.microsoft.com/library/windows/desktop/ms533798)。

##  <a name="top"></a> 部分

本演练包含以下各节：

- [创建 MFC 应用程序](#application)

- [实现 Mandelbrot 应用程序的序列化版本](#serial)

- [从用户界面线程中移除工作](#removing-work)

- [提高绘制性能](#performance)

- [添加取消支持](#cancellation)

##  <a name="application"></a> 创建 MFC 应用程序

本部分介绍如何创建基本的 MFC 应用程序。

### <a name="to-create-a-visual-c-mfc-application"></a>若要创建 Visual c + + MFC 应用程序

1. 在 **“文件”** 菜单上，单击 **“新建”**，然后单击 **“项目”**。

1. 在**新的项目**对话框中**已安装的模板**窗格中，选择**Visual c + +**，然后在**模板**窗格中，选择**MFC 应用程序**。 例如，键入项目的名称`Mandelbrot`，然后单击**确定**以显示**MFC 应用程序向导**。

1. 在中**应用程序类型**窗格中，选择**单个文档**。 絋粄**文档/视图体系结构支持**清除复选框。

1. 单击**完成**以创建项目并关闭**MFC 应用程序向导**。

     验证应用程序已成功创建，可以通过生成并运行它。 若要在生成应用程序，**构建**菜单上，单击**生成解决方案**。 如果成功生成了应用程序，通过单击运行该应用程序**开始调试**上**调试**菜单。

##  <a name="serial"></a> 实现 Mandelbrot 应用程序的序列化版本

本部分介绍如何绘制 Mandelbrot 不规则图形。 此版本将 Mandelbrot 不规则图形绘制到 GDI +[位图](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-bitmap)对象，然后将该位图的内容复制到客户端窗口。

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>若要实现 Mandelbrot 应用程序的序列化版本

1. 在 stdafx.h 中，添加以下`#include`指令：

     [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. 在 ChildView.h 之后,`pragma`指令，定义`BitmapPtr`类型。 `BitmapPtr`类型可使一个指向`Bitmap`对象共享的多个组件。 `Bitmap`时不再被引用的任何组件删除对象。

     [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. 在 ChildView.h，将以下代码添加到`protected`一部分`CChildView`类：

     [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. 在 ChildView.cpp，注释掉或删除以下行。

     [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

     在调试版本中此步骤可防止应用程序使用`DEBUG_NEW`与 GDI + 不兼容的分配器。

1. 在 ChildView.cpp，添加`using`指令`Gdiplus`命名空间。

     [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. 将以下代码添加到构造函数和析构函数的`CChildView`类来初始化和关闭 GDI +。

     [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. 实现 `CChildView::DrawMandelbrot` 方法。 此方法为指定绘制 Mandelbrot 不规则图形`Bitmap`对象。

     [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. 实现 `CChildView::OnPaint` 方法。 此方法调用`CChildView::DrawMandelbrot`，然后将复制的内容`Bitmap`到窗口的对象。

     [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

9. 验证已成功更新应用程序通过生成并运行它。

下图显示了 Mandelbrot 应用程序的结果。

![Mandelbrot 应用程序](../../parallel/concrt/media/mandelbrot.png "mandelbrot 集合")

每个像素计算的计算成本高昂，因为 UI 线程无法处理其他消息，直到完成整体计算。 这可能会降低应用程序中的响应能力。 但是，您可以通过从 UI 线程中移除工作来缓解此问题。

[[返回页首](#top)]

##  <a name="removing-work"></a> 从 UI 线程中移除工作

本部分演示如何从 Mandelbrot 应用程序中的 UI 线程中移除绘图工作。 通过将绘制工作从 UI 线程移动到工作线程，UI 线程可以处理消息，工作线程在后台生成映像。

并发运行时提供三种方式来运行任务：[任务组](../../parallel/concrt/task-parallelism-concurrency-runtime.md)，[异步代理](../../parallel/concrt/asynchronous-agents.md)，并[轻量级任务](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 虽然可以使用这些机制的任何一个从 UI 线程中移除工作，此示例使用[concurrency:: task_group](reference/task-group-class.md)对象，因为任务组支持取消操作。 本演练更高版本使用取消来减少客户端窗口调整大小时，执行的工作量并销毁窗口时执行清理。

此示例还使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)对象，以允许 UI 线程和工作线程进行相互通信。 工作线程生成的图像后，它将发送一个指向`Bitmap`对象传递给`unbounded_buffer`对象，然后将对 UI 线程绘制消息。 在 UI 线程然后接收来自`unbounded_buffer`对象`Bitmap`对象，并将其绘制到客户端窗口。

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>若要从 UI 线程中移除绘图工作

1. 在 stdafx.h 中，添加以下`#include`指令：

     [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. 在 ChildView.h，添加`task_group`并`unbounded_buffer`到成员变量`protected`一部分`CChildView`类。 `task_group`对象包含的任务的执行绘制;`unbounded_buffer`对象保留已完成的 Mandelbrot 映像。

     [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. 在 ChildView.cpp，添加`using`指令`concurrency`命名空间。

     [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. 在`CChildView::DrawMandelbrot`方法，在调用`Bitmap::UnlockBits`，调用[concurrency:: send](reference/concurrency-namespace-functions.md#send)函数来传递`Bitmap`到 UI 线程的对象。 然后画图将消息发布到 UI 线程，并使工作区无效。

     [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. 更新`CChildView::OnPaint`方法来接收更新后`Bitmap`对象，并在客户端窗口中绘制图像。

     [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

     `CChildView::OnPaint`方法创建生成 Mandelbrot 映像，如果不存在消息缓冲区中的任务。 将不包含的消息缓冲区`Bitmap`对象在情况下，如初始绘制消息和另一个窗口移动客户端窗口的前面。

1. 验证已成功更新应用程序通过生成并运行它。

UI 是现在响应速度更快，因为在后台执行绘制工作。

[[返回页首](#top)]

##  <a name="performance"></a> 提高绘制性能

Mandelbrot 不规则图形的新一代是并行化的良好候选项，因为每个像素的计算是独立于其他所有计算。 若要并行化绘制过程，将转换的外部`for`循环`CChildView::DrawMandelbrot`方法的调用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法，如下所示。

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

位图的每个元素的计算是独立的因为您无需同步访问的位图内存的绘制操作。 这样，性能将随着数目的可用的处理器的增加而扩展。

[[返回页首](#top)]

##  <a name="cancellation"></a> 添加取消支持

本部分介绍如何处理重设窗口大小以及如何销毁窗口时取消任何活动的绘制任务。

文档[PPL 中的取消](cancellation-in-the-ppl.md)说明取消运行时中的工作方式。 取消是协作性;因此，它不会立即发生。 若要停止已取消的任务，则运行时会引发过程从任务的后续调用到运行时中出现内部异常。 上一节演示如何使用`parallel_for`算法以提高性能的绘制任务。 对调用`parallel_for`使运行时停止任务，并因此使取消工作。

### <a name="cancelling-active-tasks"></a>正在取消活动任务

Mandelbrot 应用程序创建`Bitmap`对象的维度匹配客户端窗口的大小。 每次客户端窗口调整大小时，应用程序创建一项额外的后台任务以生成新的窗口大小的图像。 应用程序不需要这些中间映像;最后一个窗口大小需要唯一的映像。 若要防止此应用程序执行这一附加工作，可以取消任何活动的绘制任务中的消息处理程序`WM_SIZE`和`WM_SIZING`后调整窗口大小，然后重新计划绘制和消息将起作用。

若要调整窗口大小时取消活动的绘制任务，应用程序调用[concurrency::task_group::cancel](reference/task-group-class.md#cancel)中的处理程序方法`WM_SIZING`和`WM_SIZE`消息。 处理程序`WM_SIZE`消息还调用[task_group](reference/task-group-class.md#wait)方法以等待所有活动任务完成，然后重新计划绘制任务的更新后的窗口大小。

客户端窗口被破坏，很好的做法取消任何活动的绘制任务。 正在取消任何活动的绘制任务可确保工作线程客户端窗口被销毁后不会发布到 UI 线程的消息。 应用程序将取消任何活动的绘制任务的处理程序中`WM_DESTROY`消息。

### <a name="responding-to-cancellation"></a>响应取消操作

`CChildView::DrawMandelbrot`方法，用于执行绘制任务，必须响应取消。 运行时使用异常处理来取消任务，因为`CChildView::DrawMandelbrot`方法必须使用异常安全机制来保证，所有资源已正确清除。 此示例使用*资源获取即初始化*(RAII) 模式，以保证取消任务时，不锁定位图位。

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>若要在 Mandelbrot 应用程序中添加取消支持

1. 在 ChildView.h，在`protected`一部分`CChildView`类中，添加声明`OnSize`， `OnSizing`，和`OnDestroy`消息映射函数。

     [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. 在 ChildView.cpp，修改要包含的处理程序的消息映射`WM_SIZE`， `WM_SIZING`，和`WM_DESTROY`消息。

     [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. 实现 `CChildView::OnSizing` 方法。 此方法将取消任何现有的绘制任务。

     [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. 实现 `CChildView::OnSize` 方法。 此方法取消任何现有的绘制任务，并创建新的绘图任务更新的客户端窗口大小。

     [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. 实现 `CChildView::OnDestroy` 方法。 此方法将取消任何现有的绘制任务。

     [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. 在 ChildView.cpp，定义`scope_guard`类，该类实现 RAII 模式。

     [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. 将以下代码添加到`CChildView::DrawMandelbrot`方法之后调用`Bitmap::LockBits`:

     [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

     此代码通过创建处理取消`scope_guard`对象。 对象离开范围时，它将取消锁定位图位。

1. 修改的最终`CChildView::DrawMandelbrot`方法关闭`scope_guard`对象但不锁定，位图位之后的任何消息发送到 UI 线程之前。 这可确保不锁定位图位之前不会更新 UI 线程。

     [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. 验证已成功更新应用程序通过生成并运行它。

当您调整窗口的大小时，绘制工作执行仅为最后一个窗口大小。 销毁窗口时，也会取消任何活动的绘制任务。

[[返回页首](#top)]

## <a name="see-also"></a>请参阅

[并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)
