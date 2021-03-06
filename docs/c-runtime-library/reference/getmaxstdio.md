---
title: _getmaxstdio | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getmaxstdio
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getmaxstdio
- getmaxstdio
dev_langs:
- C++
helpviewer_keywords:
- files [C++], number open
- _getmaxstdio function
- getmaxstdio function
- open files, getting number
ms.assetid: 700ca8ce-4a8c-4e00-9467-dfa9d6b831a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2030937806eedbf1abe671032da75c531fdd5ca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396779"
---
# <a name="getmaxstdio"></a>_getmaxstdio

返回在 I/O 流级别允许同时打开的文件数。

## <a name="syntax"></a>语法

```C
int _getmaxstdio( void );
```

## <a name="return-value"></a>返回值

返回一个数字，表示在当前允许同时打开的文件数**stdio**级别。

## <a name="remarks"></a>备注

使用[_setmaxstdio](setmaxstdio.md)配置在允许同时打开的文件数量**stdio**级别。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_getmaxstdio**|\<stdio.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_setmaxstdio.c
// The program retrieves the maximum number
// of open files and prints the results
// to the console.

#include <stdio.h>

int main()
{
   printf( "%d\n", _getmaxstdio());

   _setmaxstdio(2048);

   printf( "%d\n", _getmaxstdio());
}
```

```Output
512
2048
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
