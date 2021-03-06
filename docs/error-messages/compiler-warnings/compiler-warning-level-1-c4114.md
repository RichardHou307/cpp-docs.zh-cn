---
title: 编译器警告 （等级 1） C4114 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4114
dev_langs:
- C++
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8d67148c2b9fb22c90013905eb246bf8d3bdf75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067557"
---
# <a name="compiler-warning-level-1-c4114"></a>编译器警告 （等级 1） C4114

多次使用同一类型限定符

类型声明或定义使用类型限定符 (**const**，**易失性**，**签名**，或者**无符号**) 不止一次。 这将导致具有 Microsoft 扩展 (/Ze) 的警告和 ANSI 兼容性 (/Za) 错误。

下面的示例生成 C4114:

```
// C4114.cpp
// compile with: /W1 /c
volatile volatile int i;   // C4114
```

下面的示例生成 C4114:

```
// C4114_b.cpp
// compile with: /W1 /c
static const int const * ii;   // C4114
static const int * const iii;   // OK
```
