---
title: alloca |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0c73abcb52b991ee6bd4de839861aa4ef684181
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702741"
---
# <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md)必须是 16 字节对齐，此外还要求使用帧指针。

堆栈分配需要包含低于其参数的随后被调用的函数，如中所述[堆栈分配](../build/stack-allocation.md)。

## <a name="see-also"></a>请参阅

[堆栈使用](../build/stack-usage.md)