---
title: 将弹出菜单连接到 c + + 应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- menus [C++], pop-up
- shortcut menus [C++], connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f1ebb5e2151fe770e6a59210ac564237155fafd4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412075"
---
# <a name="connecting-a-pop-up-menu-to-your-c-application"></a>将弹出菜单连接到 c + + 应用程序

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>将弹出菜单连接到应用程序

1. （例如） 添加 WM_CONTEXTMENU 消息处理程序。 有关详细信息，请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。

2. 将以下代码添加到消息处理程序：

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md)传递的消息处理程序是屏幕坐标。

## <a name="requirements"></a>要求

MFC

## <a name="see-also"></a>请参阅

[创建弹出菜单](../windows/creating-pop-up-menus.md)<br/>
[菜单编辑器](../windows/menu-editor.md)  