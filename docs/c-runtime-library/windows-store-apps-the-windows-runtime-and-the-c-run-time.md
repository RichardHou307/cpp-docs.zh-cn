---
title: UWP 应用、Windows 运行时和 C 运行时 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78f76b6f61eb5d8e7370e61e9cc1f466bdfb4c43
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592714"
---
# <a name="uwp-apps-the-windows-runtime-and-the-c-run-time"></a>UWP 应用、Windows 运行时和 C 运行时

通用 Windows 平台 (UWP) 应用是一些程序，它们在 Windows 8 上执行的 Windows 运行时中运行。 Windows 运行时是一个控制函数、变量以及可用于 UWP 应用的资源的可信环境。 但依据设计，Windows 运行时限制会阻止在 UWP 应用中使用大多数 C 运行库 (CRT) 功能。

Windows 运行时不支持以下 CRT 功能：

- 与不受支持的功能相关的大多数 CRT 函数。

   例如，UWP 应用无法使用 exec 和 spawn 系列的例程创建过程。

   对于 CRT 函数在 UWP 应用中不受支持的情况，其参考文章中会进行说明。

- 大多数多字节字符和字符串函数。

   但是，支持 Unicode 和 ANSI 文本。

- 控制台应用和命令行参数。

   但是，传统桌面应用仍支持控制台和命令行参数。

- 环境变量。

- 当前工作目录的概念。

- 静态链接到 CRT 且使用 [/MT](../build/reference/md-mt-ld-use-run-time-library.md) 或 `/MTd` 编译器选项生成的 UWP 应用和 DLL。

   即，使用多线程、静态版本的 CRT 的应用。

- 使用 [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) 编译器选项生成的应用。

   即，多线程的特定于 DLL 的调试版本的 CRT。 此类应用在 Windows 运行时中不受支持。

有关不适用于 UWP 应用的 CRT 函数的完整列表和替代函数的建议，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="see-also"></a>请参阅

[兼容性](../c-runtime-library/compatibility.md)<br/>
[Windows 运行时不支持的 CRT 函数](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)<br/>
[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
