---
title: 如何： 修改本机函数中的引用类 |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- platform invoke, reference class
- reference types, modifying in a C++ native function
ms.assetid: c701145b-62a0-4c4b-b32a-db8d69a59720
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e60b820975c76f5a5e89051b2676291b03ed6f00
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409803"
---
# <a name="how-to-modify-reference-class-in-a-native-function"></a>如何：修改本机函数中的引用类

可以将具有 CLR 数组的引用类传递给本机函数，并修改类，使用 PInvoke 服务。

## <a name="example"></a>示例

编译以下本机库。

```
// modify_ref_class_in_native_function.cpp
// compile with: /LD
#include <stdio.h>
#include <windows.h>

struct S {
   wchar_t* str;
   int intarr[2];
};

extern "C"  {
   __declspec(dllexport) int bar(S* param) {
      printf_s("str: %S\n", param->str);
      fflush(stdin);
      fflush(stdout);
      printf_s("In native: intarr: %d, %d\n",
                param->intarr[0], param->intarr[1]);
      fflush(stdin);
      fflush(stdout);
      param->intarr[0]=300;param->intarr[1]=400;
      return 0;
    }
};
```

## <a name="example"></a>示例

编译以下程序集。

```
// modify_ref_class_in_native_function_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, CharSet = CharSet::Unicode)]
ref class S  {
public:
   [MarshalAsAttribute(UnmanagedType::LPWStr)]
   String ^ str;
   [MarshalAsAttribute(UnmanagedType::ByValArray,
        ArraySubType=UnmanagedType::I4, SizeConst=2)]
   array<Int32> ^ intarr;
};

[DllImport("modify_ref_class_in_native_function.dll",
           CharSet=CharSet::Unicode)]
int bar([In][Out] S ^ param);

int main() {
   S ^ param = gcnew S;
   param->str = "Hello";
   param->intarr = gcnew array<Int32>(2);
   param->intarr[0] = 100;
   param->intarr[1] = 200;
   bar(param);   // Call to native function
   Console::WriteLine("In managed: intarr: {0}, {1}",
                       param->intarr[0], param->intarr[1]);
}
```

```Output
str: Hello
In native: intarr: 100, 200
In managed: intarr: 300, 400
```

## <a name="see-also"></a>请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)