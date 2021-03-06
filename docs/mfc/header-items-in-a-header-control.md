---
title: 标头控件中的标头项 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], header items in
- header items in header controls [MFC]
- CHeaderCtrl class [MFC], header items in
- controls [MFC], header
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21f1893861c5cb6a134cffa75806cc53eadaf059
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442365"
---
# <a name="header-items-in-a-header-control"></a>标题控件中的标题项

有相当大的控制权的外观和行为的构成标头控件的标头项 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md))。 每个标题项可以有一个字符串、一个位图化图像、一个关联图像列表中的图像或一个与之关联的应用程序定义的 32 位值。 字符串、位图或图像显示在标题项中。

您可以自定义外观和新的项的内容时就会创建调用[cheaderctrl:: Insertitem](../mfc/reference/cheaderctrl-class.md#insertitem)或通过修改现有的项，通过调用[cheaderctrl:: Getitem](../mfc/reference/cheaderctrl-class.md#getitem)并[Cheaderctrl:: Setitem](../mfc/reference/cheaderctrl-class.md#setitem)。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [自定义标题项的外观](../mfc/customizing-the-header-item-s-appearance.md)

- [对标题控件中的项排序](../mfc/ordering-items-in-the-header-control.md)

- [为标题项提供拖放支持](../mfc/providing-drag-and-drop-support-for-header-items.md)

- [标头控件使用图像列表](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)

