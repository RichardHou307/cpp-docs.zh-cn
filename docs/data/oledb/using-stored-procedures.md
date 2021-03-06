---
title: 使用存储的过程 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7b68e7494303e06245a713abc8f1d6e0424773e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114639"
---
# <a name="using-stored-procedures"></a>使用存储过程

存储的过程是存储在数据库中的可执行对象。 调用存储的过程是类似于调用 SQL 命令。 在数据源 （而不是执行或准备客户端应用程序中的语句） 上使用存储的过程可以提供多项优点，包括更高的性能、 减少的网络开销，并可提高的一致性和准确性。  
  
存储的过程可以有任意数量的 （包括零个） 输入或输出参数，并可以传递返回值。 可以将值硬编码参数为特定的数据值，也可以使用参数标记 (问号？)。  
  
> [!NOTE]
>  CLR 必须使用编译使用 Visual c + + 创建的存储的过程的 SQL Server`/clr:safe`编译器选项。  
  
OLE DB 访问接口的 SQL Server (SQLOLEDB) 支持以下存储过程使用可返回数据的机制：  
  
- 该过程中的每个 SELECT 语句生成的结果集。  
  
- 该过程可以返回通过输出参数的数据。  
  
- 该过程可具有整数返回代码。  
  
> [!NOTE]
>  你无法将存储的过程的 OLE DB 访问接口用于 Jet 因为该提供程序不支持存储的过程;只允许使用常量查询字符串中。  
  
## <a name="see-also"></a>请参阅  

[使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)