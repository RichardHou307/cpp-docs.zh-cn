---
title: auto_handle::swap |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_handle::swap
- auto_handle.swap
- auto_handle::swap
- msclr..auto_handle.swap
dev_langs:
- C++
helpviewer_keywords:
- auto_handle::swap
ms.assetid: 3ebf82d7-9b69-4a72-a22d-69b4f640f9b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: be6e791fb6e4249a05953b1a521dda72abc5db79
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443990"
---
# <a name="autohandleswap"></a>auto_handle::swap

交换与另一个对象`auto_handle`。

## <a name="syntax"></a>语法

```
void swap(
   auto_handle<_element_type> % _right
);
```

#### <a name="parameters"></a>参数

*（_r)*<br/>
`auto_handle`要与其交换对象。

## <a name="example"></a>示例

```
// msl_auto_handle_swap.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1 = "string one";
   auto_handle<String> s2 = "string two";

   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
   s1.swap( s2 );
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
}
```

```Output
s1 = 'string one', s2 = 'string two'
s1 = 'string two', s2 = 'string one'
```

## <a name="requirements"></a>要求

**标头文件** \<msclr\auto_handle.h >

**Namespace** msclr

## <a name="see-also"></a>请参阅

[auto_handle 成员](../dotnet/auto-handle-members.md)<br/>
[swap 函数 (auto_handle)](../dotnet/swap-function-auto-handle.md)