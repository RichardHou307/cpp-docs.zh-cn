---
title: 编译器错误 C3887 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3887
dev_langs:
- C++
helpviewer_keywords:
- C3887
ms.assetid: a7e82426-ef99-437b-9562-2822004e18fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1238f648c7e5481127562d34dde193a278c3cf0f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047624"
---
# <a name="compiler-error-c3887"></a>编译器错误 C3887

var: literal 数据成员的初始值设定项必须是常量表达式

一个[文字](../../windows/literal-cpp-component-extensions.md)只能使用常量表达式进行初始化数据成员。

下面的示例生成 C3887:

```
// C3887.cpp
// compile with: /clr
ref struct Y1 {
   static int i = 9;
   literal
   int staticConst = i;   // C3887
};
```

可能的解决方法：

```
// C3887b.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   int staticConst = 9;
};
```