---
title: HandleT 类 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Get
- corewrappers/Microsoft::WRL::Wrappers::HandleT::handle_
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
- corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
- corewrappers/Microsoft::WRL::Wrappers::HandleT::~HandleT
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleT class
- Microsoft::WRL::Wrappers::HandleT::Attach method
- Microsoft::WRL::Wrappers::HandleT::Close method
- Microsoft::WRL::Wrappers::HandleT::Detach method
- Microsoft::WRL::Wrappers::HandleT::Get method
- Microsoft::WRL::Wrappers::HandleT::handle_ data member
- Microsoft::WRL::Wrappers::HandleT::HandleT, constructor
- Microsoft::WRL::Wrappers::HandleT::InternalClose method
- Microsoft::WRL::Wrappers::HandleT::IsValid method
- Microsoft::WRL::Wrappers::HandleT::operator= operator
- Microsoft::WRL::Wrappers::HandleT::~HandleT, destructor
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ae6e7c1ec602cb57df071ecac24a0ac084331c3c
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162316"
---
# <a name="handlet-class"></a>HandleT 类

表示对象的句柄。

## <a name="syntax"></a>语法

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>参数

*HandleTraits*<br/>
实例[HandleTraits](../windows/handletraits-structure.md)定义句柄的共同特征的结构。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称     | 描述
-------- | -----------------------------
`Traits` | `HandleTraits` 的同义词。

### <a name="public-constructors"></a>公共构造函数

名称                                | 描述
----------------------------------- | --------------------------------------------------
[Handlet:: Handlet](#handlet)        | 初始化 `HandleT` 类的新实例。
[HandleT:: ~ HandleT](#tilde-handlet) | 取消初始化的实例`HandleT`类。

### <a name="public-methods"></a>公共方法

名称                         | 描述
---------------------------- | ----------------------------------------------------------------------
[Handlet:: Attach](#attach)   | 将指定的句柄与当前相关联`HandleT`对象。
[Handlet:: Close](#close)     | 关闭当前`HandleT`对象。
[Handlet:: Detach](#detach)   | 取消关联当前`HandleT`对象从其基础句柄。
[Handlet:: Get](#get)         | 获取基础句柄的值。
[Handlet:: Isvalid](#isvalid) | 指示是否当前`HandleT`对象表示的句柄。

### <a name="protected-methods"></a>受保护的方法

名称                                     | 描述
---------------------------------------- | ------------------------------------
[Handlet:: Internalclose](#internalclose) | 关闭当前`HandleT`对象。

### <a name="public-operators"></a>公共运算符

名称                                   | 描述
-------------------------------------- | ----------------------------------------------------------------------------------
[Handlet:: Operator =](#operator-assign) | 将指定的值移`HandleT`对象与当前`HandleT`对象。

### <a name="protected-data-members"></a>受保护的数据成员

name                        | 描述
--------------------------- | ----------------------------------------------------------------
[Handlet:: Handle_](#handle) | 包含由表示的句柄`HandleT`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HandleT`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="tilde-handlet"></a>HandleT:: ~ HandleT

取消初始化的实例`HandleT`类。

```cpp
~HandleT();
```

## <a name="attach"></a>Handlet:: Attach

将指定的句柄与当前相关联`HandleT`对象。

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>参数

*h*<br/>
句柄。

## <a name="close"></a>Handlet:: Close

关闭当前`HandleT`对象。

```cpp
void Close();
```

### <a name="remarks"></a>备注

是当前的基础句柄`HandleT`处于关闭状态，并且`HandleT`设置为无效状态。

如果句柄关闭不正确，则调用线程中将引发异常。

## <a name="detach"></a>Handlet:: Detach

取消关联当前`HandleT`对象从其基础句柄。

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>返回值

基础句柄。

### <a name="remarks"></a>备注

此操作完成后，当前`HandleT`设置为无效状态。

## <a name="get"></a>Handlet:: Get

获取基础句柄的值。

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>返回值

句柄。

## <a name="handle"></a>Handlet:: Handle_

包含由表示的句柄`HandleT`对象。

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlet"></a>Handlet:: Handlet

初始化 `HandleT` 类的新实例。

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()  
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>参数

*h*<br/>
句柄。

### <a name="remarks"></a>备注

第一个构造函数初始化`HandleT`不是有效的句柄到对象的对象。 第二个构造函数创建一个新`HandleT`参数从对象*h*。

## <a name="internalclose"></a>Handlet:: Internalclose

关闭当前`HandleT`对象。

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>返回值

**true**如果当前`HandleT`关闭成功; 否则为**false**。

### <a name="remarks"></a>备注

`InternalClose()` 为 `protected`。

## <a name="isvalid"></a>Handlet:: Isvalid

指示是否当前`HandleT`对象表示的句柄。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>返回值

**true**如果`HandleT`表示的句柄; 否则为**false**。

## <a name="operator-assign"></a>Handlet:: Operator =

将指定的值移`HandleT`对象与当前`HandleT`对象。

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>参数

*h*<br/>
将右值引用的句柄。

### <a name="return-value"></a>返回值

对当前的引用`HandleT`对象。

### <a name="remarks"></a>备注

此操作将使失效`HandleT`参数指定的对象*h*。
