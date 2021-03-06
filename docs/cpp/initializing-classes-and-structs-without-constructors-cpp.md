---
title: 初始化类和结构而无需构造函数 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9cf80b9b1a6a7002e4176720cf12b305592c6fb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117512"
---
# <a name="initializing-classes-and-structs-without-constructors-c"></a>在没有构造函数的情况下初始化类和结构 (C++)

并不总是需要为类定义构造函数，特别是相对比较简单的类。 用户可以使用统一初始化来初始化类或结构的对象，如下面的示例所示：

```cpp
#include "stdafx.h"
#include <Windows.h>

// No constructor
struct TempData
{
    int StationId;
    time_t time;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       minTemp(minimum), maxTemp(maximum), current(cur), stationId(id), time(t) {}
    int stationId;
    time_t time;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    // Member initialization (in order of declaration):
    TempData td{ 45978, GetCurrentTime(), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    //Error C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, GetCurrentTime() };

    return 0;
}
```

请注意，当类或结构具有没有构造函数，您提供将成员声明的类中的顺序列表元素。 如果类具有构造函数，提供按参数顺序的元素。

## <a name="see-also"></a>请参阅

[类和结构](../cpp/classes-and-structs-cpp.md)<br/>
[构造函数](../cpp/constructors-cpp.md)