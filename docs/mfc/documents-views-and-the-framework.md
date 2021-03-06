---
title: 文档、 视图和框架 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document templates [MFC], template objects
- applications [MFC]
- MFC, application framework
- application objects [MFC], relation to other MFC objects
- documents [MFC]
- MFC, documents
- document objects [MFC], in relation to other MFC objects
- view objects [MFC], relation to other MFC objects
- MFC, views
- document/view architecture [MFC], about document/view architecture
- objects [MFC], MFC applications
- MFC object relationships
- thread objects [MFC]
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8213ac8d45b2981a7b945fb0af0a590cf7974a8a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402351"
---
# <a name="documents-views-and-the-framework"></a>文档、视图和框架

MFC 框架的核心是文档和视图的概念。 文档是用户在编辑会话中与之进行交互的数据对象。 创建由**新建**或**打开**命令**文件**菜单并且通常保存在文件中。 (标准 MFC 文档类派生`CDocument`，与活动文档和 OLE 复合文档不同。)视图是用户可用来与文档进行交互的窗口对象。

一个正在运行的应用程序中的关键对象有：

- 一个文档或多个文档。

     您的文档类 (派生自[CDocument](../mfc/reference/cdocument-class.md)) 指定应用程序的数据。

     如果在应用程序中需要 OLE 功能，派生文档类从[COleDocument](../mfc/reference/coledocument-class.md)或其派生的类，具体取决于所需的功能的类型之一。

- 一个视图或多个视图。

     视图类 (派生自[CView](../mfc/reference/cview-class.md)) 是用户的"窗口的数据。" 视图类控制用户查看文档的数据并与之交互的方式。 在某些情况下，您可能希望一个文档拥有多个数据视图。

     如果需要滚动，派生[CScrollView](../mfc/reference/cscrollview-class.md)。 如果您的视图具有对话框模板资源中布局的用户界面，派生[CFormView](../mfc/reference/cformview-class.md)。 对于简单的文本数据，使用或派生自[CEditView](../mfc/reference/ceditview-class.md)。 对于一个基于窗体的数据访问应用程序，如数据输入程序，请从派生[CRecordView](../mfc/reference/crecordview-class.md) （针对 ODBC)。 此外提供了类[CTreeView](../mfc/reference/ctreeview-class.md)， [CListView](../mfc/reference/clistview-class.md)，并[CRichEditView](../mfc/reference/cricheditview-class.md)。

- 框架窗口

     视图显示在“文档框架窗口”中。 在 SDI 应用程序中，文档框架窗口也是应用程序的“主框架窗口”。 在 MDI 应用程序中，文档窗口是显示在主框架窗口中的子窗口。 派生的主框架窗口类指定包含您的视图的框架窗口的样式和其他特性。 如果需要自定义框架窗口，请从派生[CFrameWnd](../mfc/reference/cframewnd-class.md)自定义 SDI 应用程序的文档框架窗口。 派生自[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)以自定义 MDI 应用程序的主框架窗口。 此外从派生类[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)自定义每种不同的应用程序支持的 MDI 文档框架窗口。

- 一个或多个文档模板

     文档模板可协调文档、视图和框架窗口的创建。 一种特定的文档模板类，派生自类[CDocTemplate](../mfc/reference/cdoctemplate-class.md)、 创建和管理一种类型的所有打开的文档。 支持多种文档类型的应用程序具有多个文档模板。 使用类[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) SDI 应用程序，或使用类[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)为 MDI 应用程序。

- 应用程序对象

     应用程序类 (派生自[CWinApp](../mfc/reference/cwinapp-class.md)) 控件的所有上述对象并指定应用程序的行为，例如初始化和清理。 应用程序仅有的一个应用程序对象为应用程序支持的任何文档类型创建和管理文档模板。

- 线程对象

     如果应用程序创建不同的执行线程 — 例如，若要在后台执行计算，将使用派生自类[CWinThread](../mfc/reference/cwinthread-class.md)。 [CWinApp](../mfc/reference/cwinapp-class.md)本身派生自`CWinThread`和应用程序中表示主线程的执行 （或主进程）。 还可以在辅助线程中使用 MFC。

在一个正在运行的应用程序中，这些对象以协作方式响应用户操作（由命令和其他消息绑定在一起）。 一个应用程序对象管理一个或多个文档模板。 每个文档模板创建并管理一个或多个文档（具体取决于应用程序是 SDI 还是 MDI）。 用户通过包含在框架窗口中的视图查看和操作文档。 下图演示了 SDI 应用程序的这些对象之间的关系。

![正在运行的 SDI 应用程序中的对象](../mfc/media/vc386v1.gif "vc386v1")中运行的 SDI 应用程序的对象

本系列文章的其他部分介绍了框架工具、MFC 应用程序向导和资源编辑器如何创建这些对象，如何协同工作以及如何在编程中使用它们。 中更详细地讨论了文档、 视图和框架窗口[窗口对象](../mfc/window-objects.md)并[文档/视图体系结构](../mfc/document-view-architecture.md)。

## <a name="see-also"></a>请参阅

[使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)
