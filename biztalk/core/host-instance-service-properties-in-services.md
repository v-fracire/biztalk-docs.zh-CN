---
title: 主机实例服务中的服务属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8b317161-83a9-42d5-b24f-48ff1e54b94a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69be58a0edd2d834a869d75ef162b11865911c22
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984830"
---
# <a name="host-instance-service-properties-in-services"></a>“服务”中的主机实例服务属性
## <a name="host-instance-service-properties-in-services"></a>“服务”中的主机实例服务属性  
 创建 BizTalk 主机实例时，还会在“服务”中创建一个服务。 下表讨论了最常用的属性。  
  
|选项|Description|  
|------------|-----------------|  
|常规：**启动类型**|默认设置为**自动**以允许主机实例重新启动计算机时自动启动。 在生产环境中，此属性通常始终设置为**自动**。|  
|上的日志：**帐户**|设置为在配置 BizTalk 或创建新主机实例时指定的用户帐户。 当 BizTalk 和 SQL Server 位于不同计算机上时，此帐户必须为域帐户。 如果 BizTalk 和 SQL Server 位于同一计算机上，则此帐户可以为域帐户或本地帐户。|  
|恢复：**第一次失败**|默认设置为**重新启动服务**。 如果主机实例第一次意外停止，此设置将尝试重新启动主机实例。<br /><br /> 如果主机实例成功启动后立即停止，则**失败的第二个**应用属性。<br /><br /> 如果主机实例无法启动，则**失败的第二个**属性将不适用。 将不会进行任何其他的重新启动尝试。 主机实例将保持停止状态。|  
|恢复：**第二个失败**|默认设置为**重新启动服务**。 如果主机实例第二次意外停止，此设置将尝试重新启动主机实例。<br /><br /> 如果主机实例成功启动后立即停止，则**后续失败**应用属性。<br /><br /> 如果主机实例无法启动，则**后续失败**属性将不适用。 将不会进行任何其他的重新启动尝试。 主机实例将保持停止状态。|  
|恢复：**后续失败**|默认设置为**重新启动服务**。 如果主机实例第三次意外停止，此设置将尝试重新启动主机实例。<br /><br /> 如果主机实例成功启动后立即停止，则**后续失败**属性将继续应用。<br /><br /> 如果主机实例无法启动，则**后续失败**属性将不适用。 将不会进行任何其他的重新启动尝试。 主机实例将保持停止状态。|  
|恢复：**之后重新启动服务**|默认值为 1 分钟，并可以根据需要增大该值。|  
|依存关系|**所有**BizTalk 主机实例将开始之前，必须启动列出的组件。 这包括企业单一登录。 如果使用 Windows Server 2008，请参阅以下知识库文章：<br /><br /> [942284](http://support.microsoft.com/kb/942284) BizTalk Service 服务可能无法正常启动时重新启动正在运行 Windows Vista 或 Windows Server 2008 的计算机|  
  
 **请注意**服务中的 BizTalk 主机实例属性也存储在 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\BTSSvc$*BizTalkHostName*注册表项。  
  
### <a name="recovery"></a>恢复  
 当主机实例服务无法启动时，“服务”中的恢复功能并不允许进行无限制的服务重新启动尝试。 通过修改“恢复”属性，可以改进 BizTalk 主机实例的运行时间。 可能导致 BizTalk 主机实例停止的最常见情形包括：  
  
- 失去与 SQL Server 的网络连接  
  
- 内存不足异常  
  
- 访问冲突  
  
  **可能的方案**  
  
- SQL Server 意外关闭。 在此情况下，**第一次失败**属性将应用。 默认值**第一次失败**并**之后重新启动服务**1 分钟之后进行设置，次重新启动尝试。 如果 SQL Server 在 1 分钟后仍然不可用，将不进行任何其他的重新启动尝试。 主机实例将保持停止状态。  
  
- SQL Server 是群集的并且发生了故障转移。 故障转移用时超过 5 分钟。 在此方案中，默认值**第一次失败**并**之后重新启动服务**设置将尝试之后 1 分钟一次重新启动。 重新启动将会失败，因为 SQL Server 仍处于脱机状态。 因此，将不会进行任何其他的重新启动尝试。 主机实例将保持停止状态。  
  
  **建议**  
  
- 当停止 SQL Server 或故障转移 SQL 群集时，可手动停止 BizTalk 主机实例。 在 SQL Server 联机后，请重新启动主机实例。  
  
- 如果它是一种常见情况的 SQL 群集故障转移时间长于 1 分钟时间，提高**之后重新启动服务**值，使 SQL 群集处于联机状态。  
  
- 在 SQL Server 维护由非 BizTalk 管理员，请考虑提高**之后重新启动服务**值。 非 BizTalk 管理员可能会停止/启动 SQL Server，而没有意识到其对 BizTalk 的影响。  
  
## <a name="see-also"></a>请参阅  
 [管理 BizTalk 主机和主机实例](../core/managing-biztalk-hosts-and-host-instances.md)