---
title: 编译器警告 （等级 1） C4526 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4526
dev_langs:
- C++
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed6f2da3252c27b7a84b4d5b73f7e8ba52823dd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118500"
---
# <a name="compiler-warning-level-1-c4526"></a>编译器警告（等级 1）C4526

function： 静态成员函数不能重写虚函数虚拟 function'override 被忽略，将隐藏虚函数

静态成员函数可以满足用来重写虚函数，这使得虚拟和静态成员函数的条件。

下面的代码生成 C4526:

```
// C4526.cpp
// compile with: /W1 /c
// C4526 expected
struct myStruct1 {
   virtual void __stdcall func( int ) = 0;
};

struct myStruct2: public myStruct1 {
   static void __stdcall func( int );
};
```

以下是可能的修复方法：

- 如果该函数用于重写基类的虚函数，则移除静态说明符。

- 如果该函数本来就是静态成员函数，重命名它，以便与基类虚函数不会发生冲突。