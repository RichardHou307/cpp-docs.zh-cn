---
title: 界面元素 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f8cb2a8f3ccb36f3fa1ed2bf3f81087691ce988
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404405"
---
# <a name="interface-elements"></a>界面元素

本文档介绍 Visual Studio 2008 SP1 中引入的界面元素，并还介绍了与早期版本的库之间的差异。

下图显示了通过使用新的界面元素生成的应用程序。

![MFC 功能包的示例应用程序](../mfc/media/mfc_featurepack.png "mfc_featurepack")

## <a name="window-docking"></a>停靠窗口

窗口停靠功能类似于窗口停靠在 Visual Studio 图形用户界面使用。

## <a name="control-bars-are-now-panes"></a>控件条是现在窗格

控件条现在称为窗格和派生自[CBasePane 类](../mfc/reference/cbasepane-class.md)。 在早期版本的 MFC，控件条的基类是`CControlBar`。

通常表示应用程序主框架窗口[CFrameWndEx 类](../mfc/reference/cframewndex-class.md)或[CMDIFrameWndEx 类](../mfc/reference/cmdiframewndex-class.md)。 调用主框架*停靠站点*。 窗格可以有三种类型的父项之一： 停靠站点、 停靠栏或微型框架窗口。

有两种类型的窗格： 无法调整大小和可调整大小。 可调整大小的窗格，如状态栏和工具栏，可以通过使用拆分条或滑块调整大小。 可调整大小的窗格可以形成的容器 （其中一个窗格可停靠到另一个窗格中，创建它们之间拆分器）。 但是，不能 （停靠） 停靠栏附加可调整大小的窗格。

如果你的应用程序使用无法调整大小的窗格，派生从它们[CPane 类](../mfc/reference/cpane-class.md)。  如果你的应用程序使用可调整大小的窗格，派生从[CDockablePane 类](../mfc/reference/cdockablepane-class.md)

## <a name="dock-site"></a>停靠站点

停靠站点 （或主框架窗口） 拥有所有窗格和应用程序中的微型框架窗口。 停靠站点包含[CDockingManager](../mfc/reference/cdockingmanager-class.md)成员。 此成员维护属于停靠站点的所有窗格的列表。 列表进行排序，以便创建在停靠站点的外边缘的窗格放置于列表的开头。 当框架重绘停靠站点时，它将循环对此列表并调整每个窗格，可以包括停靠站点的当前边框的布局。 您可以调用`AdjustDockingLayout`或`RecalcLayout`时必须调整停靠布局，并且 framework 将重定向到停靠管理器的此调用。

## <a name="dock-bars"></a>停靠栏

每个主框架窗口可以定位*停靠栏*沿其边框。 停靠栏是属于一个窗格[CDockSite 类](../mfc/reference/cdocksite-class.md)。 停靠栏可以接受对象派生自[CPane](../mfc/reference/cpane-class.md)，如工具栏。 若要创建停靠栏初始化主框架窗口时，调用`EnableDocking`。 若要启用自动隐藏栏，请调用`EnableAutoHideBars`。 `EnableAutoHideBars` 创建[CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)对象，并将其每个停靠栏旁边。

每个停靠栏分为停靠行。 由停靠行[CDockingPanesRow 类](../mfc/reference/cdockingpanesrow-class.md)。 停靠的每一行包含工具栏的列表。 如果用户将工具栏停靠或将某一行中的工具栏移动到另相同的停靠栏中，框架将创建一个新行并相应地，调整大小的停靠栏或其定位在工具栏上的现有行。

## <a name="mini-frame-windows"></a>微型框架 Windows

浮动窗格驻留在微型框架窗口中。 微型框架窗口由两个类： [CMDITabInfo 类](../mfc/reference/cmditabinfo-class.md)（其中包含一个窗格） 和[CMultiPaneFrameWnd 类](../mfc/reference/cmultipaneframewnd-class.md)（其中包含几个窗格）。 若要在代码中浮动窗格，请调用[CBasePane::FloatPane](../mfc/reference/cbasepane-class.md#floatpane)。 浮动窗格后，框架会自动创建一个微型框架窗口，该微型框架窗口成为浮动窗格的父级。 时浮动窗格将停靠，框架将重置其父级且浮动窗格成为停靠栏 （对于工具栏） 或停靠站点 （适用于可调整大小的窗格）。

## <a name="pane-dividers"></a>窗格分隔线

窗格分隔线 （也称为滑块或拆分条） 由[CPaneDivider 类](../mfc/reference/cpanedivider-class.md)。 当用户将窗格停靠时，框架将创建窗格的分隔线，而不考虑是否窗格停靠在停靠站点或在另一个窗格。 当一个窗格将停靠到停靠站点中时，调用窗格分隔符*默认窗格分隔符*。 默认窗格分隔符负责在停靠站点中所有停靠的窗格的布局。 停靠管理器维护一组默认窗格分隔符和窗格的列表。 停靠管理器负责所有停靠的窗格的布局。

## <a name="containers"></a>容器

所有可调整大小的窗格，停靠到对方时, 保留在容器中。 表示容器[CPaneContainer 类](../mfc/reference/cpanecontainer-class.md)。 每个容器都有指向其左窗格中，右窗格中，左子容器、 正确的子容器和拆分器左侧和右侧部分之间。 (*左侧*并*右*并不指物理方面，但而不是识别树状结构的分支。)以这种方式我们可以构建的窗格和拆分条的树，并因此实现复杂的可以一起调整大小的窗格的布局。 `CPaneContainer`类维护容器树; 它还维护两个窗格和滑块驻留在此树中的列表。 窗格容器管理器通常嵌入到默认滑块和执行多个窗格的微型框架窗口中。

## <a name="auto-hide-control-bars"></a>自动隐藏控件条

默认情况下，每个`CDockablePane`支持自动隐藏功能。 当用户单击的标题上的固定按钮`CDockablePane`，框架将窗格切换到自动隐藏模式。 若要处理单击，框架将创建[CMFCAutoHideBar 类](../mfc/reference/cmfcautohidebar-class.md)和一个[CMFCAutoHideButton 类](../mfc/reference/cmfcautohidebutton-class.md)与关联`CMFCAutoHideBar`对象。 该框架将新`CMFCAutoHideBar`上[CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)。 该框架还会将附加`CMFCAutoHideButton`到工具栏。 [CDockingManager 类](../mfc/reference/cdockingmanager-class.md)维护`CDockablePane`。

## <a name="tabbed-control-bars-and-outlook-bars"></a>选项卡式的控件条和 Outlook 栏

[CMFCBaseTabCtrl 类](../mfc/reference/cmfcbasetabctrl-class.md)实现可拆分的选项卡的选项卡式窗口的基本功能。 若要使用`CMFCBaseTabCtrl`对象，初始化[CBaseTabbedPane 类](../mfc/reference/cbasetabbedpane-class.md)在应用程序中。 `CBaseTabbedPane` 派生自`CDockablePane`和维护一个指向`CMFCBaseTabCtrl`对象。 `CBaseTabbedPane`使用户可以停靠和调整大小选项卡式的控件条。 使用[cdockablepane:: Attachtotabwnd](../mfc/reference/cdockablepane-class.md#attachtotabwnd)动态创建停靠和选项卡式控件条。

Outlook 栏控件还基于选项卡式条。 [CMFCOutlookBar 类](../mfc/reference/cmfcoutlookbar-class.md)派生自`CBaseTabbedPane`。 有关如何使用 Outlook 栏的详细信息，请参阅[CMFCOutlookBar 类](../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="see-also"></a>请参阅

[概念](../mfc/mfc-concepts.md)

