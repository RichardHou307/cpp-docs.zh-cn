---
title: 编译器错误 C3489 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3489
dev_langs:
- C++
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b1631c9be33204edfa697cb349148d274fe30e6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081216"
---
# <a name="compiler-error-c3489"></a>编译器错误 C3489

当默认捕获模式为按值捕获时，要求使用“var”

当你指定 lambda 表达式的默认捕获模式是按值捕获时，不能按值将变量传递给该表达式的捕获子句。

### <a name="to-correct-this-error"></a>更正此错误

- 不要显式将变量传递给捕获子句，或者

- 不要将按值捕获指定为默认捕获模式，或者

- 将按引用捕获指定为默认捕获模式，或者

- 按引用将变量传递给捕获子句。 （这可能会更改 lambda 表达式的行为。）

## <a name="example"></a>示例

下面的示例将生成 C3489。变量 `n` 按值出现在默认模式为按值捕获的 lambda 表达式的捕获子句中：

```
// C3489a.cpp

int main()
{
   int n = 5;
   [=, n]() { return n; } (); // C3489
}
```

## <a name="example"></a>示例

下面的示例演示 C3489 的四种可能解决方法：

```
// C3489b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass n to the capture clause.
   [=]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-value as the default capture mode.
   [n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-reference as the default capture mode.
   [&, n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by reference to the capture clause.
   [&n]() { return n; } ();
}
```

## <a name="see-also"></a>请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)