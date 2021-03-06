---
title: RaiseException 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
dev_langs:
- C++
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 12032318f898b2986b64d5cd8a1e611a31d1fc8c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372387"
---
# <a name="raiseexception-function"></a>RaiseException 函数

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>参数

*hr*<br/>
异常引发; 异常代码也就是说，操作失败的 HRESULT。

*dwExceptionFlags*<br/>
一个标志，指示持续性异常 （标志值为零） 或 noncontinuable 异常 （标志值为非零）。 默认情况下，例外情况是了不可继续操作。

## <a name="remarks"></a>备注

引发调用线程中的异常。

有关详细信息，请参阅 Windows`RaiseException`函数。

## <a name="requirements"></a>要求

**标头：** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)