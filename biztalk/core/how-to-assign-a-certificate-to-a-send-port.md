---
title: 如何为发送端口分配证书 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, assigning
- managing [send ports], certificates
- assigning certificates
- certificates, send ports
ms.assetid: ba9e9c8b-f5b6-4fee-9e89-31b0f1df6ed4
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd09d2a646f33a65cc7c9a6319c6af2b650b6d81
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995262"
---
# <a name="how-to-assign-a-certificate-to-a-send-port"></a>如何为发送端口分配证书
本主题将介绍如何使用 BizTalk Server 管理控制台为发送端口分配安全证书。 在运行 BizTalk Server 的计算机上的“其他人”证书存储中必须有证书，否则不会处理与此发送端口关联的消息并记录错误。  
  
> [!NOTE]
>  应用程序开发人员可以通过在开发过程中使用本主题中的过程来为发送端口分配安全证书。  
  
## <a name="prerequisites"></a>必要條件  
 若要执行本主题中的过程，必须是 BizTalk Server Administrators 组的成员的帐户登录。 有关详细的权限的信息，请参阅[用于部署和管理 BizTalk 应用程序所需权限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-assign-a-certificate-to-a-send-port"></a>为发送端口分配证书  
  
1. 单击**启动**，单击**所有程序**，单击[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然后单击**BizTalk Server 管理**。  
  
2. 在控制台树中，展开要为其分配证书的发送端口所属的 BizTalk 组和 BizTalk 应用程序。  
  
3. 展开**发送端口**，右键单击发送端口，单击**属性**，然后单击**证书**。  
  
4. 如果证书存在于本地计算机上，单击**浏览**，浏览到你想要将分配到此发送端口，然后单击该证书**确定**。 否则，跳过此步骤。  
  
   > [!NOTE]
   >  即使本地计算机上有证书，如果在另一台计算机上运行 BizTalk Server，则该计算机上必须也有证书，发送端口才能处理消息。  
  
5. 如果证书中不存在本地计算机上**指纹**框中，键入或粘贴证书指纹，然后单击**确定**。 证书指纹的格式为 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 为十六进制数。  
  
## <a name="see-also"></a>请参阅  
 [创建和配置发送端口](../core/creating-and-configuring-send-ports.md)