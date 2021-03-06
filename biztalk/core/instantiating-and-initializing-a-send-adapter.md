---
title: 实例化和初始化发送适配器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f10e6507-3351-4173-95f5-48546ca5f5c4
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b91bb59d974d68595e53c563311c74f590d33b3d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978918"
---
# <a name="instantiating-and-initializing-a-send-adapter"></a>实例化和初始化发送适配器
默认情况下，在第一个消息传送到发送适配器之前，不会实例化发送适配器，这一过程称为“懒创建”。 默认的“懒创建”方法有助于节省系统资源。 创建发送适配器之后，在停止 BizTalk Server 服务之前该发送适配器将一直被缓存并且处于活动状态。  
  
 **InitTransmitterOnServiceStart**的成员**功能**枚举指示消息引擎在服务启动，而不是使用默认延迟创建，创建发送适配器如果这所需。  
  
 在消息的批处理方面，消息的发送是一个不同于消息接收的模型。 对于接收，适配器的传入消息将插入到从消息引擎获得的某个批。 对于发送，消息引擎从适配器获得批并将要传输的消息发送到适配器。 这两种情况都使用传输代理来获取消息批对象。  
  
## <a name="how-a-send-adapter-is-initialized"></a>如何初始化发送适配器  
 若要启用对传输代理的配置和绑定，适配器必须实现以下配置接口：  
  
- **IBTTransport**  
  
- **IBaseComponent**  
  
- **IBTTransportControl**  
  
- **IPersistPropertyBag**  
  
  以下步骤介绍了在初始化发送适配器时所涉及事件的顺序：  
  
1. 当消息引擎初始化发送适配器时，它首先会执行**QueryInterface**有关**IPersistPropertyBag**，这是一个可选接口。 如果适配器实现了接口，处理程序配置传递给适配器**负载**方法调用。 适配器将使用此信息来确保它得到正确地配置。  
  
2. 消息引擎执行**QueryInterface**有关**IBTTransportControl**，这是必需的接口。  
  
3. 引擎将调用**IBTTransportControl.Initialize**、 传入适配器的传输代理。  
  
4. 消息引擎执行**QueryInterface**有关**IBTTransmitter**。  
  
    如果消息引擎找到该接口，则适配器将被视为不支持批的发送器。  
  
    如果消息引擎不会发现此接口，消息引擎将执行**QueryInterface**有关**IBTBatchTransmitter**，发现其中表示适配器是可识别批发送器。  
  
    如果消息引擎找不到这两个接口中的任何一个，则会出现错误，从而导致初始化失败。 如果未找到任何必需接口，则初始化将失败。  
  
   下图说明了 API 调用的顺序；蓝色的接口由适配器实现。  
  
   ![](../core/media/transmit-adapter-init.gif "Transmit_adapter_init")  
  
   适配器在初始化和配置完毕后就可发送消息。  
  
   下图显示了初始化发送适配器时所涉及的对象交互。  
  
   ![](../core/media/ebiz-sdk-devadapter10.gif "ebiz_sdk_devadapter10")  
   初始化发送适配器的工作流  
  
> [!NOTE]
>  适配器不应阻止消息引擎在调用如**IBTTransportControl.Initialize**并**ipersistpropertybag.load 这样**。 在这些调用中执行过多的处理会影响服务启动时间。