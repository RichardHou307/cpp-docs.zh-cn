---
title: 编译器错误 C2452 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2452
dev_langs:
- C++
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c8785a8ce77849805d9620b412493accd8b8690
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087001"
---
# <a name="compiler-error-c2452"></a>编译器错误 C2452

type: safe_cast 的源类型无效

源类型[safe_cast](../../windows/safe-cast-cpp-component-extensions.md)无效。  例如中的所有类型`safe_cast`操作必须是 CLR 类型。

下面的示例生成 C2452:

```
// C2452.cpp
// compile with: /clr

struct A {};
struct B : public A {};

ref struct C {};
ref struct D : public C{};

int main() {
   A a;
   safe_cast<B*>(&a);   // C2452

   // OK
   C ^ c = gcnew C;
   safe_cast<D^>(c);
}
```