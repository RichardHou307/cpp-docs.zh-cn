---
title: 链接器工具错误 LNK2023 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2023
dev_langs:
- C++
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d8deaf8bfb10d3ceb56380560320ebb2cf9a7b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090316"
---
# <a name="linker-tools-error-lnk2023"></a>链接器工具错误 LNK2023

错误的 dll 或入口点\<dll 或入口点 >

链接器正在加载 msobj90.dll 的不正确版本。 请确保 link.exe 和 msobj90.dll 路径中的具有相同的版本。

Msobj90.dll 的依赖项可能不存在。 Msobj90.dll 的依赖项列表是：

- Msvcr90.dll

- Kernel32.dll

检查计算机中，以便 msobj90.dll 可能过时的任何其他副本。