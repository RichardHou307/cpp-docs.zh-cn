---
title: -Zl （省略默认库名） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
dev_langs:
- C++
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f09abebb8fc142bbe2390f61d790a5885c9aebe
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707312"
---
# <a name="zl-omit-default-library-name"></a>/Zl（省略默认库名）

省略.obj 文件中的默认 C 运行时库名称。 默认情况下，编译器将库的名称放入 .obj 文件中以将链接器定向到正确的库。

## <a name="syntax"></a>语法

```
/Zl
```

## <a name="remarks"></a>备注

默认库的详细信息，请参阅[使用运行时库](../../build/reference/md-mt-ld-use-run-time-library.md)。

可以使用 **/Zl**你打算将放入一个库的.obj 文件进行编译。 虽然省略库名称节省仅少量空间来容纳单一.obj 文件，但保存的总空间至关重要，在包含许多对象模块库中。

此选项是一个高级的选项。 设置此选项移除可能所必需的应用程序，从而导致链接时错误，如果你的应用程序依赖于这种支持某些 C 运行时库支持。 如果使用此选项必须提供某种其他方式所需的组件。

使用[/NODEFAULTLIB （忽略库）](../../build/reference/nodefaultlib-ignore-libraries.md)。 若要指示链接器忽略所有.obj 文件中的库引用。

有关详细信息，请参阅 [ CRT 库功能](../../c-runtime-library/crt-library-features.md)。

使用编译时 **/Zl**，`_VC_NODEFAULTLIB`定义。  例如：

```
// vc_nodefaultlib.cpp
// compile with: /Zl
void Test() {
   #ifdef _VC_NODEFAULTLIB
      int i;
   #endif

   int i;   // C2086
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**高级**属性页。

1. 修改**省略默认库名称**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)