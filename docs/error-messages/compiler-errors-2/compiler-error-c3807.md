---
title: 编译器错误 C3807 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3807
dev_langs:
- C++
helpviewer_keywords:
- C3807
ms.assetid: 7e2b0aab-8c61-4e71-b9c1-fcaeb6a1b5ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7531d5e758828a83bc94ed88b137033182bbfea6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041100"
---
# <a name="compiler-error-c3807"></a>编译器错误 C3807

type： 具有 ComImport 特性的类不能从 type2 派生，允许仅接口实现

派生自的类型<xref:System.Runtime.InteropServices.ComImportAttribute>只能实现一个接口。

## <a name="example"></a>示例

下面的示例生成 C3807。

```
// C3807.cpp
// compile with: /clr /c
ref struct S {};
interface struct I {};

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 : S {};   // C3807
ref struct S2 : I {};
```