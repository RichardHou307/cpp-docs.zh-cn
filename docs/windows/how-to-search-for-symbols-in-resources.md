---
title: 如何： 在资源 （c + +） 中的搜索符号 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b4adac3b4e593ab19287e21e5a965f3a28d008b8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427610"
---
# <a name="how-to-search-for-symbols-in-resources-c"></a>如何： 在资源 （c + +） 中的搜索符号

### <a name="to-find-symbols-in-resources"></a>在资源中查找符号

1. 从**编辑**菜单中，选择**查找符号**。

2. 在中[查找符号对话框](/visualstudio/ide/go-to)，在**查找内容**框中，从下拉列表中选择以前的搜索字符串或键入想要查找 （例如 ID_ACCEL1） 的加速键。

   > [!TIP]
   > 若要使用[正则表达式](/visualstudio/ide/using-regular-expressions-in-visual-studio)为你的搜索，必须使用[在文件中查找](/visualstudio/ide/reference/find-command)从**编辑**而不是菜单**查找符号**命令。 若要启用正则表达式，必须具有**使用： 正则表达式**中所选的复选框[查找对话框](/visualstudio/ide/finding-and-replacing-text)。 然后，您可以单击右侧的向右箭头按钮**查找内容**框，以显示搜索正则表达式的列表。 当从此列表中选择一个表达式时，它将替换中的搜索文本**查找内容**框。

3. 选择任一**查找**选项。

4. 单击**查找下一个**。

   > [!NOTE]
   > 无法搜索字符串、快捷键或二进制资源中的符号。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源，并分配的资源字符串应用于属性。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[符号：资源标识符](../windows/symbols-resource-identifiers.md)<br/>
[资源文件](../windows/resource-files-visual-studio.md)<br/>
[资源编辑器](../windows/resource-editors.md)