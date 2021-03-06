---
title: MQSeries 适配器消息流 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, message flow
ms.assetid: aa5c8523-afd6-4181-9c11-a150857a7790
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49f861b47457c0f24faf4667c9f22b93b2c8034b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013926"
---
# <a name="mqseries-adapter-message-flow"></a>MQSeries 适配器消息流
消息源自[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]计算机首先会传递到 MQSeries 服务器在 Windows 上运行。 运行在 Windows 上的 MQSeries 服务器可以位于运行 BizTalk Server 的同一计算机上。 消息通过 MQSeries Server for Windows 计算机路由至操作系统上（如 UNIX）的 MQSeries 服务器主机。 随后，应用程序将从 MQSeries 队列中检索消息。  

 来自应用程序的消息首先将进入 MQSeries 服务器上的 MQSeries 队列中。 MQSeries 服务器将该消息转发到 MQSeries Server for Windows 计算机。 BizTalk Server 从 MQSeries Server for Windows 计算机接收消息，并将其转发给相应的应用程序。  

 MQSeries 适配器支持以下消息传送方案：  


|        **应用场景**        |                                                                                                                                                                                                                 **Description**                                                                                                                                                                                                                 |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Receive           |                                                                                                                                           适配器从 MQSeries 服务器、 传递给接收一条消息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。                                                                                                                                           |
| 发送（静态单向端口） |                                                                                                                                                      适配器路由来自消息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。                                                                                                                                                      |
|        动态发送        |                                                                                                                                                                                   使应用程序能够在运行时选择目标地址 (URI)。                                                                                                                                                                                    |
|      动态接收       |                                                                                                                             使应用程序能够在运行时选择源地址 (URI)，通过设置**MQSeries.DynamicReceive**上下文属性设置为**是**并指定动态接收地址。                                                                                                                             |
|        Correlation         | 来自适配器的消息与可以处理多种类型消息的特定业务流程实例相关。<br /><br /> MQSeries 服务器可以通过使用要求响应来创建相关标识符，或者 BizTalk Server 可以创建相关标识符。<br /><br /> 有关关联集的详细信息，请参阅[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]帮助。 |

 有关使用端口和管道、 业务流程和基于内容的路由中的适配器的详细信息，请参阅[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]帮助。 在适配器中使用相关标识符的详细信息，请参阅[关联的消息使用请求-答复](../core/correlating-messages-using-request-reply.md)。  

 有关可用于在适配器中进行筛选的标头属性的信息，请参阅[与 BizTalk Server 相关的属性](../core/properties-related-to-biztalk-server.md)并[MQSeries 上下文属性](../core/mqseries-context-properties.md)。  

## <a name="see-also"></a>请参阅  
 [使用 MQSeries 适配器](../core/using-the-mqseries-adapter.md)