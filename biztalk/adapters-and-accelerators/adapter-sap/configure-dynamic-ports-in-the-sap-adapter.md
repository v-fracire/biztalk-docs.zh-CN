---
title: SAP 适配器配置动态端口 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic ports, configuring
- configuring, dynamic ports
ms.assetid: 4d6569f9-e513-47f3-b2c1-4c21bafb2bf2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de45553cfad2db19cfe16bbcd55420019b4971e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971502"
---
# <a name="configure-dynamic-ports-in-the-sap-adapter"></a>SAP 适配器配置动态端口
## <a name="use-message-context-properties"></a>使用消息上下文属性
在中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，可以配置有关的动态端口[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]。 因为[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]是基于 WCF 的适配器，您可以动态地配置的端口[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]通过使用消息上下文属性。  
  
 有关[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，URI、 操作和绑定可能会确定传入消息上的属性和在表达式形状中，然后指定，如下面的示例中所示：  
  
```  
Request2=Request1;  
Request2(WCF.Action)="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET";  
Request2(WCF.BindingType)="sapBinding";  
Request2(WCF.UserName)="YourUserName";  
Request2(WCF.Password)="YourPassword";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="sap://CLIENT=800;LANG=EN;@A/YourSAPHost/00";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
  
```  
  
> [!NOTE]
>  使用中的 WCF-SAP 适配器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理控制台中，您还可以指定的传输类型为`SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SAPAdapter"`，其中**SAPAdapter**是添加中的 WCF SAP 适配器的名称[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理控制台。  
  
 在前面的示例：  
  
- 正在从 Request1 消息创建请求 2 消息。 两条消息将映射到操作架构，这在生成使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  
  
- 发送端口是 BizTalk 业务流程中的逻辑发送端口的名称。  
  
  在表达式形状是 BizTalk 业务流程的一部分。 在部署业务流程时，还会创建 Wcf-custom 发送端口。  
  
  配置动态端口的详细信息，请参阅[配置动态发送端口使用 WCF 适配器上下文属性](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)。
  
## <a name="see-also"></a>请参阅  
[生成块以创建 SAP 应用程序](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)