---
title: 编译器错误 C3634 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3634
dev_langs:
- C++
helpviewer_keywords:
- C3634
ms.assetid: fd09f10c-f863-483b-9756-71c16b760b02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3a8ef6c2b1f57e09a62e8f08efc2a4cc1f6e2e3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110570"
---
# <a name="compiler-error-c3634"></a>编译器错误 C3634

function： 不能定义托管或 WinRTclass 的抽象方法

可在托管或 WinRT 类中声明一个抽象方法，但不能定义它。

## <a name="example"></a>示例

以下示例生成 C3634：

```
// C3634.cpp
// compile with: /clr
ref class C {
   virtual void f() = 0;
};

void C::f() {   // C3634 - don't define managed class' pure virtual method
}
```
