---
title: -WINMDKEYCONTAINER （指定密钥容器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKEYCONTAINER
dev_langs:
- C++
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d48a0966b974b1a264b4d2b539f5861ce0dfd57
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716815"
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER（指定密钥容器）

指定用于对 Windows 元数据 (.winmd) 文件进行签名的密钥容器。

```
/WINMDKEYCONTAINER:name
```

## <a name="remarks"></a>备注

类似于[/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)应用于 (.winmd) 文件的链接器选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**链接器**文件夹。

1. 选择**Windows 元数据**属性页。

1. 在中**Windows 元数据密钥容器**框中，输入位置。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)