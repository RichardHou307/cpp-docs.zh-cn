---
title: CSimpleArrayEqualHelperFalse 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6cc489850ea8e8d2704c92d1c2a671557a4db67a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084323"
---
# <a name="csimplearrayequalhelperfalse-class"></a>CSimpleArrayEqualHelperFalse 类

此类是一个帮助程序对于[CSimpleArray](../../atl/reference/csimplearray-class.md)类。

## <a name="syntax"></a>语法

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>参数

*T*<br/>
在派生的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|（静态）返回 false。|

## <a name="remarks"></a>备注

此特征类是对的补充`CSimpleArray`类。 It 始终返回 false，和另外，将调用`ATLASSERT`参数为 false，如果曾经引用它。 在相等性测试不足够定义位置的情况下，此类允许数组，其中包含元素，针对多数方法正常运行但失败，如依赖于比较的方法的定义完善的方式[CSimpleArray::查找](../../atl/reference/csimplearray-class.md#find)。

## <a name="requirements"></a>要求

**标头：** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelperFalse::IsEqual

返回 false。

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>返回值

返回 false。

### <a name="remarks"></a>备注

此方法始终返回 false，并将调用`ATLASSERT`false 如果引用的参数。 用途`CSimpleArrayEqualHelperFalse::IsEqual`是强制方法使用的比较时尚未充分定义相等性测试，以明确定义的方式失败。

## <a name="see-also"></a>请参阅

[CSimpleArrayEqualHelper 类](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
