---
title: CL 调用链接器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed6c968b86192ae79c0c921f8b3fababc596c9a2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713825"
---
# <a name="cl-invokes-the-linker"></a>CL 调用链接器

CL 编译除非使用 /c 选项后会自动调用链接器。 CL 将传递给链接器在编译过程中创建的.obj 文件的名称和命令行上指定的任何其他文件的名称。 链接器使用 LINK 环境变量中列出的选项。 可以使用 /link 选项指定 CL 命令行上的链接器选项。 请按照 /link 选项的选项重写 LINK 环境变量中。 下表中的选项禁止显示链接。

|选项|描述|
|------------|-----------------|
|/c|编译但不链接|
|/ E，/EP，/P|预处理时不编译或链接|
|/Zg|生成函数原型|
|/Zs|检查语法|

有关链接的更多详细信息，请参阅[链接器选项](../../build/reference/linker-options.md)。

## <a name="example"></a>示例

假设您正在编译三个 C 源代码文件： MAIN.c、 MOD1.c 和 MOD2.c。 每个文件包含对不同文件中定义的函数的调用：

- MAIN.c 调用函数`func1`MOD1.c 和函数中`func2`MOD2.c 中。

- MOD1.c 调用标准库函数`printf_s`和`scanf_s`。

- MOD2.c 调用名为图形函数`myline`和`mycircle`，其中一个名为 MYGRAPH.lib 库中定义。

若要生成此程序，使用以下命令行进行编译：

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

CL 首先编译 C 源文件，并创建 MAIN.obj、 MOD1.obj 和 MOD2.obj 对象文件。编译器会在每个.obj 文件中提供的标准库的名称。 有关更多详细信息，请参阅[使用运行时库](../../build/reference/md-mt-ld-use-run-time-library.md)。

CL 到链接器传递.obj 文件，以及 MYGRAPH.lib，名称的名称。 链接器解析外部引用，如下所示：

1. 在 MAIN.obj，对引用`func1`解决使用 MOD1.obj; 中的定义对引用`func2`解决使用 MOD2.obj 中的定义。

1. 在 MOD1.obj，对引用`printf_s`和`scanf_s`解决 MOD1.obj 中名为链接器查找在库中使用的定义。

1. 在 MOD2.obj，对引用`myline`和`mycircle`解决 MYGRAPH.lib 中使用的定义。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)