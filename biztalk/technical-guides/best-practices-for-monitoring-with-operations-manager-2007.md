---
title: 使用 Operations Manager 2007 监视的最佳实践 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a5026c-ef59-498b-9bef-ea0f1c932eae
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d099ba9ea60fd8f553d4eaf2011e93a054f59e68
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018693"
---
# <a name="best-practices-for-monitoring-with-operations-manager-2007"></a>监视使用 Operations Manager 2007 的最佳做法
遵循本主题以有效地监视使用 Operations Manager 2007 的应用程序中列出的最佳实践。  
  
 **安装更完整的覆盖范围的附加管理包**  
  
- 为确保 Operations Manager 2007 监视中的关键应用程序在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]环境中，应安装以下管理包：  
  
  - [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] （必需）  
  
  - Windows Server Operating System （可选）  
  
  - Microsoft Windows Server 故障转移群集 （如果群集是使用 （可选））  
  
  - SQL Server 监视  
  
  - Internet Information Services 7  
  
  - 消息队列 (MSMQ) 5.0 （可选）  
  
  **查看并确定每日警报优先级**  
  
- 每天检查警报并区分警报的优先级可确保及时解决问题。  
  
  **验证[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]与 Operations Manager 2007 服务器通信。**  
  
- 如果运行的服务器之间的通信失败[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]与监视基础结构，您将不会收到警报。  
  
  **启用和禁用规则，根据需要**  
  
- 默认情况下中的规则的一些[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理包处于禁用状态。 这些禁用的规则类型如下：需要自定义的规则，用作模板的规则，以及用于监控附加 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 事件的规则。 请确保相关的规则你[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]之外的环境。  
  
  **自定义规则根据您的环境**  
  
- 您应该自定义中的规则[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理包，以满足你[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。 某些规则需要监视阈值或时间阈值定义的最佳基于您的特定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。  
  
  **创建其他规则有必要，请根据中包含的规则[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理包**  
  
- 规则提供用于连接作为项目的创建，如模板[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主机。 在创建如下特定于项目的规则时，应将这些模板规则作为参考：  
  
  -   特定于主机的规则，例如，托管队列监视，并托管阻止监视  
  
  -   特定于 MessageBox 的规则  
  
  -   用于其他第三方组件（如 MQSeries 适配器）的规则  
  
  **监视所有 BizTalk Server 相关组件**  
  
  组件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]应监视以确保它们运行的环境包括但不是一定是限制为：  
  
- BizTalk 主机实例  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 使用安装的代理作业 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
- 为 BizTalk 解决方案开发的任何自定义服务  
  
- 为 BizTalk 解决方案开发的任何自定义数据库的状态  
  
- 与相关的任何自定义事件日志条目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]环境  
  
## <a name="see-also"></a>请参阅  
 [使用 System Center Operations Manager 2007 监视 BizTalk Server](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)