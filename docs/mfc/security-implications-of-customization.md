---
title: 自定义项的安全隐患 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 876f3b45cc9f45ab5ff1aaa7e07116482f89afc1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442079"
---
# <a name="security-implications-of-customization"></a>自定义对安全有何影响

本主题讨论了 MFC 中潜在的安全漏洞。

## <a name="potential-security-weakness"></a>潜在的安全漏洞

MFC 允许用户自定义应用程序用户界面的外观，例如，图标和按钮的外观。 MFC 还支持能够让用户执行 shell 命令的用户定义的工具。 由于应用程序的自定义设置保存在注册表的用户配置文件中，因此可能会导致安全漏洞。 任何访问该注册表的人员都可以编辑这些设置并更改应用程序的外观或行为。 例如，计算机的管理员可以通过促使用户的应用程序执行任意程序（甚至从网络共享中）来模拟用户。

## <a name="workarounds"></a>问题解决

我们建议采用以下三种方法中的任一方法来关闭注册表中的漏洞：

- 对存储在注册表中的数据进行加密。

- 将数据存储在安全文件而不是注册表中。

     若要完成第一次这两种方法之一，从派生类[CSettingsStore 类](../mfc/reference/csettingsstore-class.md)并重写其方法来实现加密或存储在注册表外的。

- 还可以在应用程序中禁用自定义。

## <a name="see-also"></a>请参阅

[MFC 自定义](../mfc/customization-for-mfc.md)

