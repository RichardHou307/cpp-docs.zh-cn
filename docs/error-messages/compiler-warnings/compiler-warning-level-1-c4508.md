---
title: 编译器警告 （等级 1） C4508 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4508
dev_langs:
- C++
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5abc1d81c3e94c02a63f73c84f3f5e5c7e9b0b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038933"
---
# <a name="compiler-warning-level-1-c4508"></a>编译器警告（等级 1）C4508

function： 函数应返回一个值;void 返回类型假定

该函数具有指定没有返回类型。 在这种情况下，也应激发 C4430 和编译器实现报告的 C4430 （默认值为 int） 的修复。

若要解决此警告，显式声明函数的返回类型。

下面的示例生成 C4508:

```
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```