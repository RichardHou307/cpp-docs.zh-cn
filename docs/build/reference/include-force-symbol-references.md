---
title: -INCLUDE （强制符号引用） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6528f6edc51a2dd01e8f91107827b570a44785de
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715775"
---
# <a name="include-force-symbol-references"></a>/INCLUDE（强制符号引用）

```
/INCLUDE:symbol
```

## <a name="parameters"></a>参数

*符号*<br/>
指定要添加到符号表中的符号。

## <a name="remarks"></a>备注

/INCLUDE 选项告知链接器将指定的符号添加到符号表。

若要指定多个符号，请键入逗号 （，）、 分号 （;） 或符号名之间有空格。 在命令行中，指定 /INCLUDE:`symbol`一次针对每个符号。

链接器解析`symbol`通过添加包含该程序的符号定义的对象。 此功能可用于包括库对象，否则将不会链接到该程序。

使用此选项指定一个符号，将覆盖由该符号的移除[/opt: ref](../../build/reference/opt-optimizations.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**输入**属性页。

1. 修改**强制符号引用**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)