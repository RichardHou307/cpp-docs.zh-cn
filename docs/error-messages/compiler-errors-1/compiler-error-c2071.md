---
title: 编译器错误 C2071 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2071
dev_langs:
- C++
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 757110c88d3279964ab0c26f753e4d3b1f2889d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025851"
---
# <a name="compiler-error-c2071"></a>编译器错误 C2071

identifier： 非法存储类

`identifier` 声明具有无效[存储类](../../c-language/c-storage-classes.md)。 为标识符指定多个存储类时或定义与存储类声明不兼容时，会导致此错误。

若要解决此问题，请了解标识符的预期的存储类 — 例如，`static`或`extern`— 并更正要匹配的声明。

## <a name="example"></a>示例

以下示例生成 C2071。

```
// C2071.cpp
// compile with: /c
struct C {
   extern int i;   // C2071
};
struct D {
   int i;   // OK, no extern on an automatic
};
```

## <a name="example"></a>示例

以下示例生成 C2071。

```
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```