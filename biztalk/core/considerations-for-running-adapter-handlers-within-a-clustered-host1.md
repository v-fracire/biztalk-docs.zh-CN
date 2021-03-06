---
title: 运行中群集 Host1 的适配器处理程序的注意事项 |Microsoft Docs
ms.custom: ''
ms.date: 2016-03-17
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- high availability
- receive adapters, clustering
- clustering, POP3 adapters
- FTP adapters, clustering
- clustering, receive adapters
- NLB system
- MSMQ send handler
- MSMQ receive handler
- clustering, FTP adapters
- handlers [adapters], best practices
- hosts, clustering
- MSMQ adapters
- clustering, MSMQ adapters
- adapters, best practices
- adapters, handlers
- POP3 adapters, clustering
- MSMQ adapters, clustering
- clustering
ms.assetid: ee66663c-4f4d-4515-9df1-aacf4fc72be4
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00436ad42634c2672560499c891ada33547f0342
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977030"
---
# <a name="considerations-for-running-adapter-handlers-within-a-clustered-host"></a>在群集主机内运行适配器处理程序的注意事项
BizTalk 主机群集支持，可用于为以下集成的 BizTalk 适配器提供高可用性： FTP 适配器、 SFTP 适配器、 MSMQ 适配器和 POP3 适配器。 使用主机群集支持还可以确保在为实现按序送达而运行适配器的单个实例时具有高可用性。  
  
 所有 BizTalk 适配器处理程序可以在群集主机上运行，但除了下面所述优点之外，在群集主机中运行适配器处理程序并没有什么其他优点。 如果您的处理要求不包括任何下面描述的方案，则应在群集主机中不运行适配器处理程序。  
  
## <a name="running-the-ftp-or-sftp-adapter-receive-handler-within-a-clustered-biztalk-host"></a>在群集的 BizTalk 主机内运行 FTP 或 SFTP 适配器接收处理程序  
 通过创建多个适配器处理程序在 BizTalk 组内不同 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 服务器的 BizTalk 主机实例上运行，可为大多数 BizTalk 服务器集成适配器实现高可用性。 但是，FTP 或 SFTP 适配器接收处理程序不应配置为同时在多个 BizTalk 主机实例中运行。 之所以提出此建议是因为 FTP 或 SFTP 接收适配器使用 FTP 或 SFTP 协议从目标系统中检索文件。 FTP 或 SFTP 协议不会锁定文件，以确保在运行 FTP 或 SFTP 接收适配器的多个实例时不会同时检索同一文件的多个副本。  
  
 为确保 FTP 或 SFTP 接收适配器的高可用性，应将 FTP 或 SFTP 接收适配器配置为在已群集的 BizTalk 主机实例中运行。  
  
## <a name="running-msmq-adapter-handlers-within-a-clustered-biztalk-host"></a>在群集 BizTalk 主机内运行 MSMQ 适配器处理程序  
 为确保 MSMQ 适配器的高可用性以及 MSMQ 适配器发送或接收的消息的事务一致性，应执行以下操作：  
  
1. 在 Windows 群集组中的群集资源配置消息队列 (MSMQ) 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]计算机。  
  
2. 将群集的 MSMQ 服务添加到群集的 BizTalk 主机的资源依存关系列表中。 这可确保在群集的 BizTalk 主机始终开始之后发生故障转移群集的 MSMQ 服务。  
  
3. 在 BizTalk 主机实例（已配置为与群集的 MSMQ 资源同属一个群集组的群集资源）中，配置 MSMQ 适配器发送和接收处理程序。  
  
   建议执行以上步骤的原因如下：  
  
   **MSMQ 适配器接收处理程序**– MSMQ 4.0 (Windows Server 2008) 之前的 MSMQ 版本不支持远程事务性读取，支持仅本地事务读取。 在这种情况下，MSMQ 适配器接收处理程序必须是本地群集的消息队列服务，以完成本地事务读取使用 MSMQ 适配器的主机实例中运行。  
  
> [!IMPORTANT]
>  MSMQ 适配器接收处理程序要求运行消息队列服务的本地非群集的实例的计算机与运行接收处理程序主机实例的计算机为同一台计算机。  
  
 **MSMQ 适配器发送处理程序**-若要确保所做的 MSMQ 适配器，使用 MSMQ 适配器发送处理程序的传出队列的事务发送的一致性，以便如果 MSMQ 服务的传出队列失败则可能应具备高可用性已恢复。 在群集组中配置群集的消息 Queuingresource 和 MSMQ 适配器处理程序将确保使用 MSMQ 适配器发送处理程序的传出队列具有高可用性。 这样可降低消息队列服务失败时发生消息丢失的可能性。  
  
> [!NOTE]
>  MSMQ 接收位置是否**仅**接收来自远程 MSMQ 服务器上的 MSMQ 队列，则可以通过运行 MSMQ 实现高可用性 BizTalk 组中接收多个 BizTalk 计算机上的主机。  若要为 MSMQ 提供高可用性，必须确保远程 MSMQ 服务器正在使用中 Windows 故障转移群集。  如果使用的事务性队列，必须运行远程 MSMQ 服务器 MSMQ 4.0 (Windows Server 2008) 或更高版本。  
  
## <a name="running-the-pop3-adapter-receive-handler-within-a-clustered-biztalk-host"></a>在群集的 BizTalk 主机内运行 POP3 适配器接收处理程序  
 POP3 适配器接收处理程序不需要配置为在群集的 BizTalk 主机中运行，除非该适配器从中进行读取的 POP3 服务器允许对同一邮箱进行多个并行连接。 如果 POP3 适配器连接到的 POP3 服务器允许对其邮箱进行多个并行连接，则建议您必须通过将单个 POP3 适配器接收处理程序配置为在已群集的 BizTalk 主机实例中运行，来为 POP3 适配器确保高可用性。 我们提出此建议的原因是，确保在运行 POP3 接收适配器的多个实例时，不会同时检索同一电子邮件的多个副本。  
  
## <a name="running-a-receive-adapter-that-supports-ordered-delivery-with-a-clustered-biztalk-host"></a>运行支持通过群集的 BizTalk 主机进行按序送达的接收适配器  
 使用 MSMQ 和 MQSeries 集成适配器，可以按照文档的接收顺序向 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提交这些文档。 此功能的正常运行需要在任意给定的时间只有这些接收适配器的单个实例处于运行状态。 为确保这些适配器的单个实例的高可用性，应将这些适配器配置为在群集的 BizTalk 主机实例中运行。