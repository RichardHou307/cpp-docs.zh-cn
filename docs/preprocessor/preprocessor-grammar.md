---
title: 预处理器语法 |Microsoft Docs
ms.custom: ''
ms.date: 09/04/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56df4d0bfdaf87ace87a9f9dcbde85166929e642
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766111"
---
# <a name="preprocessor-grammar"></a>预处理器语法

*控制行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** *标识符**令牌字符串*<sub>选择</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** <em>标识符</em>**(** *标识符*<sub>选择</sub> **，** ...**，** *标识符*<sub>选择</sub> **)** *令牌字符串*<sub>选择</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **"** *路径规范* **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **\<** *路径规范* **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#line** *数字序列***"** *filename* **"**<sub>选择  </sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#undef** *标识符*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#error** *令牌字符串*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#pragma** *令牌字符串*

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**定义 (** *标识符* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**定义***标识符*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;任何其他常量表达式

*条件*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*if 部分**命令部件*<sub>优化</sub> *else 部分*<sub>选择</sub> *endif 行*

*if 部分*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*如果行**文本*

*如果行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *常量表达式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *标识符*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *标识符*

*命令部件*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*命令行**文本*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*命令部件**命令行**文本*

*命令行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif** *常量表达式*

*其他部件*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*其他行**文本*

*其他行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*endif 行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

*数字序列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*数字*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*数字序列**数字*

*数字*： 之一<br/>
&nbsp;&nbsp;&nbsp;&nbsp;0 1 2 3 4 5 6 7 8 9

*令牌字符串*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;标记字符串

*令牌*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*关键字*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*标识符*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*常量*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*运算符*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*标点符号*

*文件名*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;合法操作系统文件名

*路径规范*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;合法文件路径

*文本*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;文本的任何序列

> [!NOTE]
> 在中展开以下非终止符[词法约定](../cpp/lexical-conventions.md)一部分*c + + 语言参考*:*常量*，*常量表达式*，*标识符*，*关键字*，*运算符*，并且*标点符号*。

## <a name="see-also"></a>请参阅

[语法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)