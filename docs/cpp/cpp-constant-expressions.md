---
title: C++ 常量表达式 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35041b3a58f53586702db73d3bc5f6103f4f7cd7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054358"
---
# <a name="c-constant-expressions"></a>C++ 常量表达式

一个*常量*值是一种不会更改。 C + + 提供了两个关键字，它们使你能够表达不打算修改对象的意图，还可让你实现该意图。

C++ 需要常量表达式（计算结果为常量的表达式）以便声明：

- 数组边界

- case 语句中的选择器

- 位域长度规范

- 枚举初始值设定项

常量表达式中合法的唯一操作数是：

- 文本

- 枚举常量

- 声明为使用常量表达式初始化的常量的值

- **sizeof**表达式

必须将非整型常量（显式或隐式）转换为常量表达式中合法的整型。 因此，以下代码是合法的：

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

到整型的显式转换在是合法的常量表达式;所有其他类型和派生的类型是非法使用作为操作数时除外**sizeof**运算符。

逗号运算符和赋值运算符不能用于常量表达式。

## <a name="see-also"></a>请参阅

[表达式类型](../cpp/types-of-expressions.md)