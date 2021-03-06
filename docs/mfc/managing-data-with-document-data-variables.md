---
title: 使用文档数据变量管理数据 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0a1db1e15733a0a3cd217c44aaaa325c146ee64
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435878"
---
# <a name="managing-data-with-document-data-variables"></a>使用文档数据变量管理数据

实现文档的数据，作为您的文档类的成员变量。 例如，随意画图程序声明类型的数据成员`CObList`-存储指向链接的列表`CObject`对象。 此列表用于存储的手画线绘图所组成的点数组。

实现文档的成员数据的方式取决于你的应用程序的性质。 若要帮助您摆脱困境，MFC 提供的一组"集合类"— 数组、 列表和映射 （字典），包括基于 c + + 模板的集合，如封装各种通用数据类型的类以及`CString`， `CRect`， `CPoint`， `CSize`，和`CTime`。 有关这些类的详细信息，请参阅[类库概述](../mfc/class-library-overview.md)中*MFC 参考*。

在定义文档的成员数据时，您通常将到文档类，以设置和获取数据的项以及执行其他有用的操作对其添加成员函数。

你的视图通过使用视图的指针，指向在创建时视图中安装的文档访问文档对象。 可以通过调用检索视图的成员函数中的此指针`CView`成员函数`GetDocument`。 请务必将该到您自己的文档类型的指针转换。 然后您可以通过指针访问公共文档成员。

如果频繁的数据传输需要直接访问权限，或者你想要使用的文档类的非公共成员，您可能想要使视图类的文档类的友元 （在 c + + 术语）。

## <a name="see-also"></a>请参阅

[使用文档](../mfc/using-documents.md)

