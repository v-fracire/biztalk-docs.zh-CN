---
title: MSMQ 适配器属性架构和属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- AcknowledgeType property [MSMQ adapters]
- MSMQ adapters, schemas
- AppSpecific property [MSMQ adapters]
- SegmentationSupport property [MSMQ adapters]
- SourceMachine property [MSMQ adapters]
- Label property, MSMQ adapters
- MSMQ adapters, properties
- TimeOut property [MSMQ adapters]
- BodyType property [MSMQ adapters]
- CorrelationId property [MSMQ adapters]
- Recoverable property [MSMQ adapters]
- Authenticated property [MSMQ adapters]
- EncryptionAlgorithm property [MSMQ adapters]
- ResponseQueue property [MSMQ adapters]
- configuring [MSMQ adapters], properties
- MaximumMessageSize property [MSMQ adapters]
- UseAuthentication property [MSMQ adapters]
- UseDeadLetterQueue property [MSMQ adapters]
- SentTime property [MSMQ adapters]
- schemas, MSMQ adapters
- TimeOutUnits property [MSMQ adapters]
- CertificateThumbPrint property [MSMQ adapters]
- Id property [MSMQ adapters]
- UseJournalQueue property [MSMQ adapters]
- MessageType property [MSMQ adapters]
- ArrivedTime property [MSMQ adapters]
- Transactional property [MSMQ adapters]
- configuring [MSMQ adapters], schemas
- Acknowledgement property [MSMQ adapters]
- Priority property [MSMQ adapters]
- AdministrationQueue property [MSMQ adapters]
ms.assetid: 9de29341-db8e-4d50-8f1d-3b7397afb58d
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 356aac0cbe7444c0b81955ae4982524606d11d54
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985382"
---
# <a name="msmq-adapter-property-schema-and-properties"></a>MSMQ 适配器属性架构和属性
MSMQ 适配器对应用程序中使用的上下文属性赋值。 有关列表发送和接收 MSMQ 适配器中的属性，请参阅[如何配置 MSMQ 接收位置](../core/how-to-configure-an-msmq-receive-location.md)并[如何配置 MSMQ 发送端口](../core/how-to-configure-an-msmq-send-port.md)。  
  
## <a name="context-properties"></a>上下文属性  
 下表列出了 MSMQ 适配器对其赋值的上下文属性：  
  
|**名称**|**类型**|**Description**|**升级**|  
|--------------|--------------|---------------------|------------------|  
|**确认**|ssNoversion|指定此消息表示的确认的分类使用中的值**System.Messaging.Acknowledgment**枚举。|“否”|  
|**AcknowledgeType**|ssNoversion|指定发送应用程序请求的确认消息的类型。|“否”|  
|**AdministrationQueue**|string|指定接收确认消息的队列的名称。|“否”|  
|**AppSpecific**|ssNoversion|指定可用于组织不同类型消息的特定于应用程序的信息。|是|  
|**ArrivedTime**|dateTime|指定消息到达目标队列的时间。|“否”|  
|**经过身份验证**|boolean|指定消息是否已验证。|“否”|  
|**BodyType**|smallint|指定消息正文包含的数据的类型。|“否”|  
|**CertificateThumbPrint**|string|指定要用于消息验证用途的客户端证书的指纹。|是|  
|**相关 Id**|string|指定确认消息、报告消息和响应消息用来引用原始消息的消息标识符。|是|  
|**EncryptionAlgorithm**|ssNoversion|指定用于对消息正文进行加密的加密算法。|“否”|  
|**Id**|string|指定消息的标识符。|“否”|  
|**标签**|string|指定应用程序定义的用于描述消息的 Unicode 字符串。|是|  
|**MaximumMessageSize**|unsignedint|指定发送给所指定队列的消息的最大大小 (KB)。|“否”|  
|**MessageType**|ssNoversion|指定消息类型。 消息队列消息可以是以下类型之一：<br /><br /> -Normal，这是发送到队列中，应用程序的典型消息或响应消息返回给发送应用程序。<br />-确认，每当发送应用程序请求一个消息队列生成的。 例如，消息队列可以生成肯定消息或否定消息，以指示原始消息已到达或已被读取。 消息队列将向发送应用程序所指定的管理队列返回相应的确认消息。<br />-报表，只要源队列管理器中定义报告队列消息队列生成的。 如果启用了跟踪，则每次原始消息进入或离开消息队列服务器时，消息队列就会向消息队列的报告队列发送报告消息。|“否”|  
|**Priority**|ssNoversion|指定消息优先级使用中定义的值**System.Messaging.MessagePriority**枚举。|是|  
|**可恢复**|boolean|指定在出现计算机故障或网络问题时是否确保消息送达。|“否”|  
|**ResponseQueue**|string|指定用于接收应用程序所生成的响应消息的队列。|“否”|  
|**SegmentationSupport**|boolean|指定是否支持大于 4 MB 的消息段。|“否”|  
|**SentTime**|dateTime|指定在源队列管理器发送消息时发送计算机上的日期和时间。|“否”|  
|**SourceMachine**|string|指定消息所源自的计算机。|“否”|  
|**TimeOut**|ssNoversion|指定消息最长可以经过多少时间到达目标队列而不引起超时。|“否”|  
|**将 TimeOutUnits**|string|指定的单位**超时**属性。 可以将该属性设置为“天”、“小时”、“分钟”或“秒”。|“否”|  
|**事务性**|boolean|指定事务性和非事务性发送端口和接收位置的行为。|“否”|  
|**UseAuthentication**|boolean|指定消息在发送之前是否已（或必须）验证。|“否”|  
|**UseDeadLetterQueue**|boolean|指定是否应将无法送达的消息的副本发送到死信队列。|“否”|  
|**UseJournalQueue**|boolean|指定是否应当在发信方计算机的计算机日志中保留消息的副本。|“否”|  
  
> [!NOTE]
>  **确认**， **AcknowledgeType**， **EncryptionAlgorithm**，以及**MessageType**属性，可以使用等效的整数中的枚举值**System.Messaging**命名空间。 有关这些值的详细信息，请参阅 .NET Framework 类库帮助中的“System.Messaging 命名空间”。  
> 
> [!NOTE]
>  如果进行开发所需的 BizTalk 项目，可让使用 MSMQ 适配器上下文属性，BizTalk 项目必须包含对文件的引用**Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties.dll**位于[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安装目录。  
  
## <a name="message-labels"></a>消息标签  
 可以使用消息队列**标签**通过添加对引用的筛选器中的属性**Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties.dll** ，然后选择中的属性**筛选器**对话框。 还可以在其他上下文中使用该属性，因为 MSMQ 适配器会自动将该属性添加到消息上下文中。  
  
## <a name="see-also"></a>请参阅  
 [配置 MSMQ 适配器](../core/configuring-the-msmq-adapter.md)