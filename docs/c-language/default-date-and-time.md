---
title: 默认日期和时间 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- time, default
- dates, default for _DATE and _TIME
ms.assetid: 2a00a772-94f9-4513-a76b-63441456c1e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61f512d82ee33e0b900d61ff4a90c18336f88a16
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020647"
---
# <a name="default-date-and-time"></a>默认日期和时间

ANSI 3.8.8 转换的日期和时间不可用时应遵循的 `__DATE__` 和 `__TIME__` 的定义

当操作系统不提供转换的时间和日期时，`__DATE__` 和 `__TIME__` 的默认值为 `May 03 1957` 和 `17:00:00`。

## <a name="see-also"></a>请参阅

[预处理指令](../c-language/preprocessing-directives.md)