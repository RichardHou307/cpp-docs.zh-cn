---
title: 重命名 (#import) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Rename
dev_langs:
- C++
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce1604e3ef7655d72a3ed692e27d6d6c9ae0cb12
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409072"
---
# <a name="rename-import"></a>重命名 (#import)
**C + + 专用**  
  
解决名称冲突问题。  
  
## <a name="syntax"></a>语法  
  
```  
rename("OldName","NewName")  
```  
  
### <a name="parameters"></a>参数  
*OldName*  
类型库中的旧名称。  
  
*新名称*  
要替代旧名称使用的名称。  
  
## <a name="remarks"></a>备注  
 
如果指定此属性，则编译器会将出现的所有*OldName*中提供的用户提供的类型库*NewName*生成的标头文件中。  
  
当类型库中的名称与系统标头文件中的宏定义一致时，可以使用此特性。 如果未解决这种情况下，则会生成各种语法错误，如[编译器错误 C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md)并[编译器错误 C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md)。  
  
> [!NOTE]
> 该替换是针对类型库中使用的名称，而不是针对生成的标头文件中的名称。  
  
例如，假设类型库中存在名为 `MyParent` 的属性，并且在标头文件中定义了宏 `GetMyParent`，在 `#import` 前面使用了该宏。 由于`GetMyParent`是错误处理的包装器函数的默认名称`get`属性，会发生名称冲突。 若要解决此问题，请在 `#import` 语句中使用以下特性：  
  
```  
rename("MyParent","MyParentX")  
```  
  
该语句对类型库中的名称 `MyParent` 重命名。 尝试对 `GetMyParent` 包装器名称重命名将失败：  
  
```  
rename("GetMyParent","GetMyParentX")  
```  
  
这是因为名称 `GetMyParent` 仅在生成的类型库标头文件中出现。  
  
**结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 
[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)