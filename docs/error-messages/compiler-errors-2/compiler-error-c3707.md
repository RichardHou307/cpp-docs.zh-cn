---
title: 编译器错误 C3707 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3707
dev_langs:
- C++
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d18d4a82d06018cdba6147ba6756b1718648847a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052774"
---
# <a name="compiler-error-c3707"></a>编译器错误 C3707

function： 调度接口方法必须有 dispid

如果您使用`dispinterface`方法，您必须将其分配`dispid`。 若要修复此错误，将分配`dispid`到`dispinterface`方法，例如，通过取消注释`id`下面的示例中的方法上的属性。 有关详细信息，请参阅属性[dispinterface](../../windows/dispinterface.md)并[id](../../windows/id.md)。

下面的示例生成 C3707:

```
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```