---
title: 编译器警告 （等级 C4208 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4208
dev_langs:
- C++
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ee87ad1d43b20c4d0a72b877b05b1ba4c084a1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064615"
---
# <a name="compiler-warning-level-4-c4208"></a>编译器警告（等级 4）C4208

使用了非标准扩展： delete [exp]-计算但忽略 exp

通过 Microsoft 扩展 (/Ze)，可以删除数组中使用括号内的某个值[delete 运算符](../../cpp/delete-operator-cpp.md)。 忽略的值。

```
// C4208.cpp
// compile with: /W4
int main()
{
   int * MyArray = new int[18];
   delete [18] MyArray;      // C4208
   MyArray = new int[18];
   delete [] MyArray;        // ok
}
```

此类值都无效 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。