---
title: 指定路径名 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 636326e5af577b4e26c61a2094fe73dd4a680f2d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402468"
---
# <a name="specifying-the-pathname"></a>指定路径名

每个输出文件选项接受*pathname*参数可以指定一个位置和输出文件的名称。 参数可以包含驱动器名称、 目录和文件的名称。 不允许有空格选项和参数之间。

如果*pathname*包括文件名称不具有扩展名，编译器将为输出默认扩展插件。 如果*pathname*包括一个目录，但任何文件名称，包括编译器创建具有指定的目录中的默认名称的文件。 默认名称基于源代码文件和输出文件的类型的默认扩展的基名称。 如果不用*pathname*编译器完全，使用默认目录中的默认名称创建一个文件。

或者， *pathname*参数可以是设备名称 （AUX、 CON、 PRN 或 NUL） 而不是文件名称。 不使用选项和设备名称或冒号之间有空格作为设备名称。

|设备名称|表示|
|-----------------|----------------|
|AUX|辅助设备|
|CON|控制台|
|PRN|打印机|
|NUL|空设备 （不创建任何文件）|

## <a name="example"></a>示例

下面的命令行发送到打印机映射文件：

```
CL /FmPRN HELLO.CPP
```

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](../../build/reference/output-file-f-options.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)