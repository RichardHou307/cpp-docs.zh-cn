---
title: 表达式语句 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f026a91846196e34f97b4d2cbcfa2c9fa749e8b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058596"
---
# <a name="expression-statement"></a>表达式语句

表达式语句导致计算表达式。 出于表达式语句的原因，不会发生控制或迭代的传输。

表达式语句的语法就是

## <a name="syntax"></a>语法

```
[expression ] ;
```

## <a name="remarks"></a>备注

在执行下一个语句前，将计算表达式语句中的所有表达式并完成所有副作用。 最常用的表达式语句是赋值和函数调用。  由于表达式是可选的因此单独的分号被视为空表达式语句，称为[null](../cpp/null-statement.md)语句。

## <a name="see-also"></a>请参阅

[ 语句概述](../cpp/overview-of-cpp-statements.md)