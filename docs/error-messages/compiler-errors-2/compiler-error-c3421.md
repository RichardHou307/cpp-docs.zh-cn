---
title: 编译器错误 C3421 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3421
dev_langs:
- C++
helpviewer_keywords:
- C3421
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 815fc64e1f2cc80440e188d944827820bd55383b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114535"
---
# <a name="compiler-error-c3421"></a>编译器错误 C3421

“type”: 由于该类的终结器不可访问或不存在，因此无法调用它

终结器属于隐式专用，因此无法从其封闭类型外调用它。

有关详细信息，请参阅[析构函数和终结器中如何： 定义和使用类和结构 (C + + CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

## <a name="example"></a>示例

下面的示例生成 C3421。

```
// C3421.cpp
// compile with: /clr
ref class A {};

ref class B {
   !B() {}

public:
   ~B() {}
};

int main() {
   A a;
   a.!A();   // C3421

   B b;
   b.!B();   // C3421
}
```