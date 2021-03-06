---
title: multi_link_registry 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
dev_langs:
- C++
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 174a168d6a22bca54fb00bf302cd7cbbc65cc961
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162329"
---
# <a name="multilinkregistry-class"></a>multi_link_registry 类

`multi_link_registry` 对象是管理多个源块或多个目标块的 `network_link_registry`。

## <a name="syntax"></a>语法

```
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

#### <a name="parameters"></a>参数

*（_b)*<br/>
块数据类型存储在`multi_link_registry`对象。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[multi_link_registry](#ctor)|构造 `multi_link_registry` 对象。|
|[~ multi_link_registry 析构函数](#dtor)|销毁`multi_link_registry`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[add](#add)|将添加一个指向`multi_link_registry`对象。 (重写[network_link_registry:: add](network-link-registry-class.md#add)。)|
|[begin](#begin)|返回一个迭代器中的第一个元素到`multi_link_registry`对象。 (重写[network_link_registry:: begin](network-link-registry-class.md#begin)。)|
|[包含](#contains)|搜索`multi_link_registry`指定块的对象。 (重写[network_link_registry:: contains](network-link-registry-class.md#contains)。)|
|[count](#count)|中的项的计数`multi_link_registry`对象。 (重写[network_link_registry:: count](network-link-registry-class.md#count)。)|
|[remove](#remove)|移除从链接`multi_link_registry`对象。 (重写[network_link_registry:: remove](network-link-registry-class.md#remove)。)|
|[set_bound](#set_bound)|链接的数量设置上限`multi_link_registry`对象可以保存。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

##  <a name="add"></a> 添加

将添加一个指向`multi_link_registry`对象。

```
virtual void add(_EType _Link);
```

### <a name="parameters"></a>参数

*链接 （_l)*<br/>
指向要添加的块的指针。

### <a name="remarks"></a>备注

该方法将引发[invalid_link_target](invalid-link-target-class.md)异常如果链接已存在在注册表中，或如果绑定已设置与`set_bound`函数和链接已被删除。

##  <a name="begin"></a> 开始

返回一个迭代器中的第一个元素到`multi_link_registry`对象。

```
virtual iterator begin();
```

### <a name="return-value"></a>返回值

中的第一个元素的迭代器`multi_link_registry`对象。

### <a name="remarks"></a>备注

最终状态由`NULL`链接。

##  <a name="contains"></a> 包含

搜索`multi_link_registry`指定块的对象。

```
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>参数

*链接 （_l)*<br/>
指向要在其中搜索中的块的指针`multi_link_registry`对象。

### <a name="return-value"></a>返回值

**true**如果未找到指定的块， **false**否则为。

##  <a name="count"></a> 计数

中的项的计数`multi_link_registry`对象。

```
virtual size_t count();
```

### <a name="return-value"></a>返回值

中的项数`multi_link_registry`对象。

##  <a name="ctor"></a> multi_link_registry

构造 `multi_link_registry` 对象。

```
multi_link_registry();
```

##  <a name="dtor"></a> ~ multi_link_registry

销毁`multi_link_registry`对象。

```
virtual ~multi_link_registry();
```

### <a name="remarks"></a>备注

该方法将引发[invalid_operation](invalid-operation-class.md)异常，如果调用之前将删除所有链接。

##  <a name="remove"></a> 删除

移除从链接`multi_link_registry`对象。

```
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>参数

*链接 （_l)*<br/>
指向块被删除，如果找到。

### <a name="return-value"></a>返回值

**true**找到该链接并将其删除，如果**false**否则为。

##  <a name="set_bound"></a> set_bound

链接的数量设置上限`multi_link_registry`对象可以保存。

```
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>参数

*_MaxLinks*<br/>
最大数目链接`multi_link_registry`对象可以保存。

### <a name="remarks"></a>备注

设置了界限后，取消某项的链接将导致 `multi_link_registry` 对象进入不可变状态，在该状态下进一步调用 `add` 将引发 `invalid_link_target` 异常。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[single_link_registry 类](single-link-registry-class.md)
