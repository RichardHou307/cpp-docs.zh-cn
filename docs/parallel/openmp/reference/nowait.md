---
title: nowait |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- nowait
dev_langs:
- C++
helpviewer_keywords:
- nowait OpenMP clause
ms.assetid: 8a74265d-879c-46cf-8071-a1084f24f16e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3fa4579aabf8a62e5117e096c5a49225451af6e7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381057"
---
# <a name="nowait"></a>nowait

重写屏障指令中隐式。

## <a name="syntax"></a>语法

```
nowait
```

## <a name="remarks"></a>备注

`nowait` 适用于以下指令：

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [部分](../../../parallel/openmp/reference/sections-openmp.md)

- [single](../../../parallel/openmp/reference/single.md)

有关详细信息，请参阅[2.4.1 for 构造](../../../parallel/openmp/2-4-1-for-construct.md)， [2.4.2 sections 构造](../../../parallel/openmp/2-4-2-sections-construct.md)，并[2.4.3 单一构造](../../../parallel/openmp/2-4-3-single-construct.md)。

## <a name="example"></a>示例

```
// omp_nowait.cpp
// compile with: /openmp /c
#include <stdio.h>

#define SIZE 5

void test(int *a, int *b, int *c, int size)
{
    int i;
    #pragma omp parallel
    {
        #pragma omp for nowait
        for (i = 0; i < size; i++)
            b[i] = a[i] * a[i];

        #pragma omp for nowait
        for (i = 0; i < size; i++)
            c[i] = a[i]/2;
    }
}

int main( )
{
    int a[SIZE], b[SIZE], c[SIZE];
    int i;

    for (i=0; i<SIZE; i++)
        a[i] = i;

    test(a,b,c, SIZE);

    for (i=0; i<SIZE; i++)
        printf_s("%d, %d, %d\n", a[i], b[i], c[i]);
}
```

```Output
0, 0, 0
1, 1, 0
2, 4, 1
3, 9, 1
4, 16, 2
```

## <a name="see-also"></a>请参阅

[子句](../../../parallel/openmp/reference/openmp-clauses.md)