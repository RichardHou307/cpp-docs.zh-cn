---
title: 编译器错误 C2505 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2505
dev_langs:
- C++
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6bd22d7a25311b14ed599c6693bfa0c7913b304
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109166"
---
# <a name="compiler-error-c2505"></a>编译器错误 C2505

symbol: __declspec(modifer) 仅应用于全局对象或静态数据成员的声明或定义

一个`__declspec`在函数中使用了旨在只能在全局范围内使用的修饰符。

有关详细信息，请参见 [应用程序域](../../cpp/appdomain.md) 和 [过程](../../cpp/process.md)。

下面的示例生成 C2505:

```
// C2505.cpp
// compile with: /clr

// OK
__declspec(process) int ii;
__declspec(appdomain) int jj;

int main() {
   __declspec(process) int i;   // C2505
   __declspec(appdomain) int j;   // C2505
}
```