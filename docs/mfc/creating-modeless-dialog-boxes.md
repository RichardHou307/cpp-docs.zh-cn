---
title: 创建无模式对话框 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77b80f66f2956e71b90e4d939a0fb74aef28edb1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407031"
---
# <a name="creating-modeless-dialog-boxes"></a>创建无模式对话框

对于无模式对话框，您必须在您的对话框类中提供自己的公共构造函数。 若要创建无模式对话框中，调用公共构造函数，，然后调用对话框对象的[创建](../mfc/reference/cdialog-class.md#create)成员函数以加载对话框资源。 您可以调用**创建**期间或之后的构造函数调用。 如果对话框资源的属性**WS_VISIBLE**，对话框将立即显示。 如果不是，必须调用其[ShowWindow](../mfc/reference/cwnd-class.md#showwindow)成员函数。

## <a name="see-also"></a>请参阅

[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

