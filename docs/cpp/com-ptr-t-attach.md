---
title: _com_ptr_t::Attach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2fbedb2bbfba16abf1196d1dba377f7589c916b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099611"
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach

**Microsoft 专用**

封装此智能指针的类型的原始接口指针。

## <a name="syntax"></a>语法

```
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>参数

*pInterface*<br/>
原始接口指针。

*fAddRef*<br/>
如果它为 TRUE，则`AddRef`调用。 如果为 FALSE 时，`_com_ptr_t`对象采用而无需调用的原始接口指针的所有权`AddRef`。

## <a name="remarks"></a>备注

- **附加 (***pInterface***)** `AddRef`不调用。 将接口的所有权传递给此 `_com_ptr_t` 对象。 `Release` 调用以减少前面封装指针的引用计数。

- **附加 (***pInterface* **，***fAddRef***)** 如果*fAddRef*为 TRUE， `AddRef`调用来增加封装的接口指针的引用计数。 如果*fAddRef*为 FALSE，这`_com_ptr_t`对象将拥有原始接口指针，而无需调用的所有权`AddRef`。 `Release` 调用以减少前面封装指针的引用计数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)