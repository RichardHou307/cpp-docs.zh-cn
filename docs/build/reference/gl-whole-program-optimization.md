---
title: -GL （全程序优化） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97561a63a21550cc06f29a95f6ddf05687758b83
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723653"
---
# <a name="gl-whole-program-optimization"></a>/GL（全程序优化）

启用全程序优化。

## <a name="syntax"></a>语法

```
/GL[-]
```

## <a name="remarks"></a>备注

全程序优化允许编译器在程序中的所有模块上执行优化的信息。 对不全程序优化的情况下执行优化每个模块编译 （单位） 的基础。

全程序优化默认情况下处于关闭状态，必须显式启用。 但是，还有可能要明确禁用其与 **/gl-隐式**。

使用所有模块的信息，编译器可以：

- 优化函数边界间的寄存器的使用。

- 更好地跟踪对全局数据，允许加载和存储的数量减少的修改。

- 更好地的跟踪一组可能的项修改通过指针取消引用，请减少数量的加载和存储。

- 即使另一个模块中定义的函数的模块中函数进行内联。

使用生成的.obj 文件 **/GL**将不可用到此类链接器实用程序进行[EDITBIN](../../build/reference/editbin-reference.md)并[DUMPBIN](../../build/reference/dumpbin-reference.md)。

如果编译您的程序与 **/GL**并[/c](../../build/reference/c-compile-without-linking.md)，应使用 /LTCG 链接器选项来创建输出文件。

[/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)不能用于 **/GL**

使用生成的文件格式 **/GL**当前版本中可能无法读取由 Visual c + + 的后续版本。 不应提供与生成的.obj 文件组成的.lib 文件 **/GL**除非您是愿意提供的所有版本的 Visual c + + 的.lib 文件副本在你希望用户使用，现在和将来。

使用生成的.obj 文件 **/GL**预编译标头文件不应该用于生成的.lib 文件，除非将生成在同一台计算机上链接的.lib 文件 **/GL** .obj 文件。 在链接时，将需要从.obj 文件的预编译的头文件的信息。

有关可用优化和全程序优化的限制的详细信息，请参阅[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。  **/GL**还可以按配置优化; 请参阅 /LTCG。  在编译时的配置文件引导式优化，如果希望从按配置优化的函数，必须使用进行编译[/Gy](../../build/reference/gy-enable-function-level-linking.md)或隐含 /Gy 编译器选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 请参阅[/LTCG （链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md)有关如何指定的信息 **/GL**开发环境中。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)