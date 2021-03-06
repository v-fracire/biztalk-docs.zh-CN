---
title: 如何创建接收调用的业务流程上的订阅 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3423309a-cb5a-40a5-9582-6ee3ac82b538
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3ccb4743b2054a02d492b053de21a32a27badaf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010302"
---
# <a name="how-to-create-receive-subscriptions-at-invoked-orchestrations"></a>如何创建接收调用的业务流程上的订阅
尽管您可以将消息传递作为参数通过**启动业务流程**形状在启动业务流程，在某些情况下，你可能想要从调用方业务流程向后调用的业务流程发送消息时调用。 例如，您可能不清楚调用时要传递什么消息，或者其他业务流程可能需要向调用的业务流程动态发送消息。  
  
 应该通过传入一个相关来向调用的业务流程发送消息，以便调用的业务流程能够创建由该相关帮助定义的订阅，然后使用该订阅来接收消息。 不过，仅仅靠传入一个相关，然后由调用的业务流程基于该相关创建订阅，再根据该订阅接收消息，还是不够的。 如果采用上述方法，从调用方业务流程发送到调用的业务流程的消息将导致错误：“无法路由发布的消息，因为找不到订户。” 原因如下：  
  
- 调用的业务流程中存在争用情况。  
  
- 不存在提交点，调用的业务流程无法向 MessageBox 数据库发送订阅以便路由，所以无法接收消息。  
  
  解决此问题的方法之一是执行以下步骤：  
  
1. 在调用方业务流程中，应具有某个激活接收以接收消息。 调用方业务流程中接收消息、 初始化相关集，并将相关集和一个自相关接收直接绑定端口通过后**启动业务流程**形状。 传入的端口将变为调用的业务流程中的发送端口，您将用该端口发回消息，以便与调用方业务流程同步。  
  
2. 在调用的业务流程中，将消息通过自相关端口发回调用方业务流程。 这样即可与调用方业务流程保持同步，避免出现争用情况，并且在向 MessageBox 创建接收订阅以便路由的过程中在调用的业务流程中提供提交点。  
  
3. 调用方业务流程通过自相关端口接收消息，并与调用的业务流程保持同步。 请注意，使用自相关端口接收消息时不需要再指定相关。 现在可以安全地从调用方业务流程向调用的业务流程发送消息，调用的业务流程将根据相关来接收消息。  
  
   尽管上述方法可以实现目标，但更好的做法是传入对接收所基于的相关进行初始化的消息。 通过自相关端口对调用方业务流程和调用的业务流程进行同步时，我们建议始终传入对相关进行初始化所需的消息。 以下步骤提供了最为可靠且性能最佳的方法：  
  
4. 在调用方业务流程中，应具有某个激活接收以接收消息。 在收到消息后，消息传递和一个自相关接收直接绑定端口穿过**启动业务流程**形状。 您传入的消息将用于在调用的业务流程中对相关进行初始化。 传入的端口将变为调用的业务流程中的发送端口，您将用该端口发回消息，以便与调用方业务流程同步。  
  
5. 在调用的业务流程中，对相关进行初始化，然后将消息发回调用方业务流程。 这样即可与调用方业务流程保持同步，避免出现争用情况，并且在向 MessageBox 创建接收订阅以便路由的过程中在调用的业务流程中提供提交点。  
  
6. 调用方业务流程通过自相关端口接收消息，并与调用的业务流程保持同步。 请注意，自相关端口接收不需要再指定相关。 现在可以安全地从调用方业务流程向调用的业务流程发送消息，调用的业务流程将根据相关来接收消息。  
  
## <a name="see-also"></a>请参阅  
 [业务流程中使用的相关性](../core/using-correlations-in-orchestrations.md)   
 [如何使用自相关直接绑定端口](../core/how-to-use-self-correlating-direct-bound-ports.md)