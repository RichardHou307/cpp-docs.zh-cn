---
title: 向后兼容性 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3056b90f3c6f0f62158a9b6dcfe145cda9740c6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092188"
---
# <a name="backward-compatibility"></a>向后兼容性

对于产品版本间的兼容性，库 OLDNAMES.LIB 将旧名称映射到新名称。 例如，`open` 将映射到 `_open`。 仅在使用以下命令行选项的组合进行编译时必须显式链接 OLDNAMES.LIB：

- `/Zl`（从对象文件中忽略默认库名称）和 `/Ze`（默认值 - 使用 Microsoft 扩展）

- `/link`（链接器控件）、`/NOD`（无默认库搜索）和 `/Ze`

有关编译器命令行选项的详细信息，请参阅[编译器参考](../build/reference/compiler-options.md)。

## <a name="see-also"></a>请参阅

[兼容性](../c-runtime-library/compatibility.md)