---
title: _acmdln、_tcmdln、_wcmdln | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _wcmdln
- _acmdln
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _acmdln
- acmdln
- _wcmdln
- wcmdln
- _tcmdln
- tcmdln
dev_langs:
- C++
helpviewer_keywords:
- _wcmdln global variable
- wcmdln global variable
- _acmdln global variable
- _tcmdln global variable
- tcmdln global variable
- acmdln global variable
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c9dd8af9b55ab022277737f2349b27eb257810f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135862"
---
# <a name="acmdln-tcmdln-wcmdln"></a>_acmdln、_tcmdln、_wcmdln

内部 CRT 全局变量。 命令行。

## <a name="syntax"></a>语法

```
char * _acmdln;
wchar_t * _wcmdln;

#ifdef WPRFLAG
   #define _tcmdln _wcmdln
#else
   #define _tcmdln _acmdln
```

## <a name="remarks"></a>备注

这些 CRT 内部变量将存储完整的命令行。 将在 CRT 的导出符号中公开它们，但不会在代码中使用它们。 `_acmdln` 将数据存储为字符字符串。 `_wcmdln` 将数据存储为宽字符字符串。 可将 `_tcmdln` 定义为 `_acmdln` 或 `_wcmdln`，具体取决于哪一个是合适的。

## <a name="see-also"></a>请参阅

[全局变量](../c-runtime-library/global-variables.md)