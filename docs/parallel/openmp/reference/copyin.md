---
title: copyin |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 424bb8eaa41e3bbb0cf697df108adcef116e1b04
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379575"
---
# <a name="copyin"></a>copyin

允许线程访问主线程的值为[threadprivate](../../../parallel/openmp/reference/threadprivate.md)变量。

## <a name="syntax"></a>语法

```
copyin(var)
```

## <a name="parameters"></a>参数

*var*<br/>
`threadprivate`并行构造之前存在的主线程中的变量的值用于初始化的变量。

## <a name="remarks"></a>备注

`copyin` 适用于以下指令：

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [部分](../../../parallel/openmp/reference/sections-openmp.md)

有关详细信息，请参阅[2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md)。

## <a name="example"></a>示例

请参阅[threadprivate](../../../parallel/openmp/reference/threadprivate.md)有关的使用示例`copyin`。

## <a name="see-also"></a>请参阅

[子句](../../../parallel/openmp/reference/openmp-clauses.md)