---
title: 编译器警告 （等级 1） C4544 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4544
dev_langs:
- C++
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7cd274f0d1b595d374e1b108db40a51395b968
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084271"
---
# <a name="compiler-warning-level-1-c4544"></a>编译器警告（等级 1）C4544

“declaration”：已忽略此模板声明中的默认模板自变量

默认模板自变量在错误的位置指定，并且已被忽略。 类模板的默认模板参数只能在类模板的声明或定义中指定，不能在类模板的成员上指定。

此示例生成 C4545，而下一个示例演示如何修复此问题：

```
// C4544.cpp
// compile with: /W1 /LD
template <class T>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T=int>
template <class T1>
struct S<T>::S1 {};   // C4544
```

在此示例中，默认参数应用于类模板 `S`：

```
// C4544b.cpp
// compile with: /LD
template <class T = int>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1 {};
```