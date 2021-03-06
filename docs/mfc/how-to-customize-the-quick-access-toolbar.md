---
title: 如何： 自定义快速访问工具栏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f3ec14971b69788892690c26ef2759f3b35d55f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419095"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>如何：自定义快速访问工具栏

快速访问工具栏 (QAT) 是一个可自定义的工具栏，其中包含一组显示在“应用程序”按钮旁边或类别选项卡下面的命令。 下图显示了一个典型的快速访问工具栏。

![MFC 功能区快速访问工具栏](../mfc/media/quick_access_toolbar.png "quick_access_toolbar")

若要自定义快速访问工具栏，请打开它**属性**窗口中，修改其命令，然后预览功能区控件。

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>在“属性”窗口中打开快速访问工具栏

1. 在 Visual Studio 中，在**视图**菜单上，单击**资源视图**。

1. 在中**资源视图**，双击要在设计图面上显示的功能区资源。

1. 在设计图面上，右键单击快速访问工具栏菜单上，然后单击**属性**。

## <a name="quick-access-toolbar-properties"></a>快速访问工具栏属性

下表定义了快速访问工具栏的属性。

|属性|定义|
|--------------|----------------|
|QAT 位置|在应用程序启动时，指定快速访问工具栏的位置。 位置可以是**上面**或**如下**功能区控件。|
|QAT 项|指定可用于快速访问工具栏的命令。|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>添加或移除快速访问工具栏上的命令

1. 在中**属性**窗口中，单击**QAT 项**，然后单击省略号按钮 **（...）**.

1. 在中**QAT 项编辑器**对话框中，使用**添加**并**删除**按钮可以修改的快速访问工具栏上的命令列表。

1. 如果希望命令显示在快速访问工具栏和“快速访问工具栏”菜单中，请选择此命令旁边的框。 如果希望命令仅显示在菜单中，请清除此框。

## <a name="previewing-the-ribbon"></a>预览功能区

快速访问工具栏命令不会显示在设计图面上。 若要查看这些命令，则必须预览功能区或运行应用程序。

#### <a name="to-preview-the-ribbon-control"></a>预览功能区控件

- 上**功能区编辑器工具栏**，单击**测试功能区**。

## <a name="see-also"></a>请参阅

[功能区设计器 (MFC)](../mfc/ribbon-designer-mfc.md)

