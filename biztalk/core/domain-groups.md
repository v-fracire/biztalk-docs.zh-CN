---
title: 域组 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9adc090e-e18c-46b6-b985-49b200d42966
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2944ce83df75ed724c9a7acafeee119b40cacafb
ms.sourcegitcommit: 7b64c823fa8d7fa8b10b163613311be69b861017
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39625865"
---
# <a name="domain-groups-in-biztalk"></a>在 BizTalk 中的域组
BizTalk Server 在单计算机配置和多计算机配置中都支持域组和域用户帐户。 对于多计算机配置，必须满足本部分以及安装指南的“多服务器环境注意事项”中提出的要求。 有关详细信息，请参阅[安装概述](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。  
  
## <a name="before-you-begin"></a>开始之前
-   如果你的 BizTalk Server 配置使用域组，则在配置 BizTalk Server 前必须先手动创建这些组。 配置管理器无法创建域组。  
  
-   创建域组和/或用户帐户之后, 将用户帐户添加到根据在组隶属关系的适当组[Windows 组和 BizTalk Server 中的用户帐户](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
-   使用 **\<DomainName\>\\< 用户名\>** 指定 Configuration Manager 中的域帐户信息时。  
  
-   对于所有群集方案，BizTalk Server 要求使用域帐户。 不能将本地帐户用于群集 SQL Server 或群集 SSO 服务器（主密钥服务器）。  
  
-   安装和配置 BizTalk Server 的管理员必须是以下组的成员：SSO Administrators（仅当配置主密钥服务器时）、本地 Administrators、sysadmin SQL Server 角色以及 OLAP Administrators。  
  
> [!NOTE]
>  如果在配置 SSO Administrators 和 SSO Affiliate Administrators 组的过程中指定了域组，并且您具有足够的权限，则会自动创建域组。 如果您没有足够的权限，请确保这些组已存在。  
  
## <a name="see-also"></a>请参阅  
 [本地组](../core/local-groups.md)   
 [安装概述](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)   
 [BizTalk Server 中的 Windows 组和用户帐户](../core/windows-groups-and-user-accounts-in-biztalk-server.md)
