---
title: 编译器警告 （等级 1） C4656 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4656
dev_langs:
- C++
helpviewer_keywords:
- C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3334b9448dd6e9d47ed0b3ee3e4dfb9dfc57b57f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032402"
---
# <a name="compiler-warning-level-1-c4656"></a>编译器警告（等级 1）C4656

symbol： 数据类型新增功能或自上次生成以来已更改或在其他地方以不同的方式定义

你添加或更改了数据类型，使其成为自上次成功生成后的源代码中的新类型。 “编辑并继续”不支持对现有数据类型的更改。

此警告将始终后跟 [错误 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 有关详细信息，请参阅 [受支持的代码更改](/visualstudio/debugger/supported-code-changes-cpp)。

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>若要在不结束当前调试会话的情况下删除此警告

1. 将数据类型改回其在发生错误前的状态。

1. 在“调试”  菜单中选择“应用代码更改” 。

### <a name="to-remove-this-error-without-changing-your-source-code"></a>若要在不更改源代码的情况下删除此错误

1. 在“调试”  菜单上，选择“停止调试” 。

1. 在“生成”  菜单上，选择“生成” 。