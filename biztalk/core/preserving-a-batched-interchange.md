---
title: 保留批的交换 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 907e07f3-1f3e-485e-a82d-b28eb7658e0a
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 887995e9a44996c57da9e36bec1c5ec3edc1cc7b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993486"
---
# <a name="preserving-a-batched-interchange"></a>保留批处理交换
本主题介绍了如何配置协议以便将批处理 EDI 交换作为单个文档处理而不是从交换拆分事务集。  
  
## <a name="prerequisites"></a>必要條件  
 必须以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理员组或 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators 组成员的身份登录。  
  
### <a name="to-configure-the-receiving-and-sending-of-a-preserved-batch"></a>配置保留的批的接收和发送  
  
1. 在中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理控制台中，单击**方**节点。 在中**参与方和业务配置文件**页上，单击具有将解析为传入批处理交换的协议的参与方。 在中**协议**部分中的页上，右键单击该协议，然后单击**属性**。 在中**协议属性**对话框单向协议选项卡 （向其解析将入站批处理的交换） 中，执行以下操作：  
  
   1.  在中**标识符**页上，输入为 ISA5、 ISA6、 ISA7 和 ISA8 的值输入值。 确保您输入了正确的值，以便传入的批处理交换解析为该协议。  
  
   2.  在中**本地主机设置**页 (下**交换设置**)，在**接收方设置**部分中，为**入站批处理选项**，选择以下选项：  
  
       -   **保留交换-出错时挂起交换**– 选择此选项可指定 BizTalk Server 应原样保留交换不变，同时创建一个 XML 文档为整个批处理交换。 选择此选项后，如果交换中的一个或多个事务集未能通过验证，BizTalk Server 将挂起整个交换。  
  
       -   **保留交换-出错时挂起事务集**– 选择此选项可指定 BizTalk Server 应原样保留交换不变，同时创建一个 XML 文档为整个批处理交换。 使用此选项，如果交换中的一个或多个事务集未能通过验证，BizTalk Server 将挂起的事务集，同时继续处理所有其他事务集。  
  
       > [!NOTE]
       >  如果您选择以上两个选项之一，则交换、组和事务集段属性（确定 BizTalk Server 将如何创建传出交换的 ISA、GS 和 ST 标头）将不适用。 被保留的交换中存在的交换、组和事务集标头将在发送管道对其执行发送前的相关处理时予以保留。 但是，如果您要使用在协议中为交换指定的值，请将 `EDI.PopulateInterchangeValues` 上下文属性设置为“true”。  
  
2. 按下列操作为保留批创建 Visual Studio 项目：  
  
   1. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，创建一个 BizTalk 项目，并为批处理内的所有消息添加架构。  
  
   2. 生成和部署项目。  
  
3. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理控制台，创建一个发送端口按照以下步骤发送保留批。  
  
   1.  发送管道设置为**EdiSend**或**AS2EdiSend**。  
  
   2.  将发送端口的筛选器设置为上下文属性 `EDI.ReuseEnvelope == True`。  
  
       > [!NOTE]
       >  设置此筛选器以确保发送端口将订阅所有保留的批处理交换。 EdiReceive 接收管道会升级上下文属性 `EDI.ReuseEnvelope` 以便将交换标识为已保留。  
  
## <a name="see-also"></a>请参阅  
 [配置 EDI 批](../core/configuring-edi-batches.md)   
 [如何创建发送端口](../core/how-to-create-a-send-port2.md)