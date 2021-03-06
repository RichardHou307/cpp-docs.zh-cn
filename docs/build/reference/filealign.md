---
title: /FILEALIGN （对齐文件中的部分） |Microsoft Docs
ms.date: 10/23/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /filealign
dev_langs:
- C++
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 630fe7014c87487a9b4df61de60ac8f5518593e0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720013"
---
# <a name="filealign-align-sections-in-files"></a>/FILEALIGN （对齐文件中的部分）

**/FILEALIGN**链接器选项可以指定部分写入到输出文件的指定大小的倍数的对齐方式。

## <a name="syntax"></a>语法

> __/FILEALIGN:__*大小*

### <a name="parameters"></a>参数

*size*<br/>
节对齐的大小以字节为单位，它必须是 2 的幂。

## <a name="remarks"></a>备注

**/FILEALIGN**选项将使链接器将对齐的倍数的边界上的输出文件中的每一部分*大小*值。 默认情况下，链接器不使用固定的对齐大小。

**/FILEALIGN**选项可用于提高磁盘利用率的效率，或将页面从磁盘加载速度更快。 较小的部分可能可用于运行在较小的设备，或者保留下载较小的应用程序。 节对齐磁盘上的不会影响在内存中的对齐方式。

使用 [DUMPBIN](dumpbin-reference.md) 可查看有关输出文件中各节的信息。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**命令行**中的属性页**链接器**文件夹。

1. 键入选项名 **/FILEALIGN:** 以及中的大小**其他选项**框。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)