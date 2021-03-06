---
title: add_pointer 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_pointer
dev_langs:
- C++
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c5f352f684818009210b4d394f4a820159da053
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101945"
---
# <a name="addpointer-class"></a>add_pointer 类

从指定类型创建指向类型的指针。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>参数

*T*<br/>
要修改的类型。

## <a name="remarks"></a>备注

该成员**typedef** `type`名称相同的类型`remove_reference<T>::type*`。 别名`add_pointer_t`是访问成员的快捷方式**typedef** `type`。

因为从引用创建指针是无效的，所以 `add_pointer` 将从指定类型中移除引用（如果有），然后再创建指向类型的指针。 因此，你可以将某一类型用于 `add_pointer`，而不必考虑该类型是否是引用。

## <a name="example"></a>示例

下面的示例演示某一类型的 `add_pointer` 与指向该类型的指针相同。

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_pointer 类](../standard-library/remove-pointer-class.md)<br/>
