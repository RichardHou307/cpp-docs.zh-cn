---
title: _CIlog10 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _CIlog10
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- CIlog10
- _CIlog10
dev_langs:
- C++
helpviewer_keywords:
- _CIlog10 intrinsic
- CIlog10 intrinsic
ms.assetid: 05d7fcaa-3cff-4cc5-8d44-015e7cacba24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf647dd583436125acf6f1649699aaecc20b287b
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234289"
---
# <a name="cilog10"></a>_CIlog10

对堆栈顶部的值执行 `log10` 运算。

## <a name="syntax"></a>语法

```
void __cdecl _CIlog10();
```

## <a name="remarks"></a>备注

此版本的 `log10` 函数具有编译器理解的专用化调用约定。 该函数将加快执行的速度，因为它可防止生成副本和帮助注册表分配。

生成的值被将被推送到堆栈顶部。

## <a name="requirements"></a>要求

**平台：** x86

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[log、logf、log10、log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)