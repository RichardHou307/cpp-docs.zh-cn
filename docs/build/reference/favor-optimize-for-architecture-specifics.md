---
title: -倾向于 （优化体系结构详细信息） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /favor
dev_langs:
- C++
helpviewer_keywords:
- -favor compiler option [C++]
- /favor compiler option [C++]
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03d1bdce12e461446f1804844040457dae6e9d43
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724748"
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor（针对体系结构详细信息优化）

**/favor:** `option`生成的代码进行了优化的特定体系结构或针对 AMD 和 Intel 体系结构中的微体系结构的详细信息。

## <a name="syntax"></a>语法

```
/favor:{blend | ATOM | AMD64 | INTEL64}
```

## <a name="remarks"></a>备注

**/favor:blend**<br/>
（x86 和 x64）生成针对 AMD 和 Intel 体系结构中的微体系结构的特性进行了优化的代码。 虽然 **/favor:blend**可能不会达到最佳性能可能特定处理器上，这为了跨范围广泛的 x86 和 x64 处理器提供最佳性能。 默认情况下 **/favor:blend**生效。

**/favor:ATOM**<br/>
（x86 和 x64）生成针对 Intel Atom 处理器和 Intel Centrino Atom 处理器的特性进行了优化的代码。 通过使用生成的代码 **/favor:ATOM**还可能产生于 Intel 处理器的 Intel SSSE3、 SSE3、 SSE2 和 SSE 指令。

**/favor:AMD64**<br/>
（仅限 x64）针对 AMD Opteron 和支持 64 位扩展的 Athlon 处理器优化生成的代码。 优化过的代码可在所有 x64兼容平台上运行。 通过使用生成的代码 **/favor:AMD64**可能导致支持 Intel64 的 Intel 处理器上会降低性能。

**/favor:INTEL64**<br/>
（仅限 x64）针对支持 Intel64 的 Intel 处理器优化生成的代码，这通常能提高平台的性能。 生成的代码可在任何 x64 平台上运行。 使用生成的代码 **/favor:INTEL64**可能导致 AMD Opteron 和支持 64 位扩展的 Athlon 处理器上会降低性能。

> [!NOTE]
> Intel64 体系结构以前称为扩展内存 64 技术和相应的编译器选项已 **/favor:EM64T**。

有关如何针对 x64 的程序的信息体系结构，请参阅[x64 软件约定](../../build/x64-software-conventions.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**C/c + +** 文件夹。

1. 选择**命令行**属性页。

1. 输入中的编译器选项**其他选项**框。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)