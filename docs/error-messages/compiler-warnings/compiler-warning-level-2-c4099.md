---
title: 编译器警告 （等级 2） C4099 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4099
dev_langs:
- C++
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d7ffee02e8e5414a0e06cc4ba0da77a50c75f53
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110167"
---
# <a name="compiler-warning-level-2-c4099"></a>编译器警告 （等级 2） C4099

identifier： 类型名称以前使用 objecttype1 现在使用 objecttype2

对象声明为结构定义为一个类，或声明为类的对象定义为结构。 编译器将使用定义中提供的类型。

## <a name="example"></a>示例

下面的示例生成 C4099。

```
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```