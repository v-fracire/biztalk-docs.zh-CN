---
title: 步骤 6： 配置 EDI-AS2 接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 167f8ba2-d38b-4088-863b-2bd90c2a12a2
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d5ec3a7c253ab37a76846962cb348cd8b203a23
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009846"
---
# <a name="step-6-configure-the-edi-as2-receive-location"></a>步骤 6： 配置 EDI-AS2 接收位置
![步骤 6 11](../core/media/tut-step6-of-11.gif "Tut_Step6_of_11")  
  
 在此步骤中，您将设置一个用于从 Fabrikam 参与方接收 EDI 消息的单向接收位置。 此接收位置使用 AS2EdiReceive 接收管道来处理传入 EDI/AS2 消息。 消息将使用 BTSHTTPReceive.dll ISAPI 扩展通过 Contoso 虚拟目录由 sender.exe 应用程序发送到该接收位置。  
  
 在此教程中，您将设置动态发送端口以异步发送 MDN 响应。 在此方案中，仅要求使用单向接收端口。 不过，您也可以更改 Sender.exe 以发送一个指定同步 MDN 的 AS2 消息。 接着，您必须创建一个双向请求响应接收端口以返回 MDN。 有关详细信息，请参阅"测试解决方案"一节[演练 (AS2): 使用同步 MDN 通过 AS2 接收 EDI](../core/walkthrough-as2-receiving-edi-over-as2-with-a-synchronous-mdn.md)。  
  
## <a name="prerequisites"></a>必要條件  
 你必须以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理员组成员的身份登录。  
  
### <a name="to-create-the-biztalk-http-receive-location"></a>创建 BizTalk HTTP 接收位置  
  
1. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理控制台中，在 BizTalk Application 1 节点中，右键单击**接收端口**，依次指向**新建**，然后单击**单向接收端口**.  
  
2. 为接收端口的名称**Receive_AS2**。  
  
3. 单击**接收位置**在控制台树中，然后单击**新建**。  
  
4. 在中**接收位置属性**对话框中，名称在接收位置**Receive_AS2**，选择**HTTP**有关**类型**，，然后单击**配置**。  
  
5. 在中**HTTP 传输属性**对话框框中，输入 **/Contoso/BTSHTTPReceive.dll**有关**虚拟目录和 ISAPI 扩展**。 清除**成功后的返回相关句柄**，然后选择**挂起失败的请求**。 单击“确定” 。  
  
6. 选择**AS2EdiReceive**有关**接收管道**。 单击**确定**，然后单击**确定**试。  
  
   > [!NOTE]
   >  AS2EdiReceive 接收管道执行 AS2 解码和 EDI 拆装。  
  
7. 在中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理控制台中，单击**接收位置**下的 BizTalk Application 1 节点中，右键单击**Receive_AS2**，然后单击**启用**.  
  
## <a name="next-steps"></a>后续步骤  
 配置发送端口 (**Send_Asynch_MDN**) 发送端口以将异步 MDN 发送回 Fabrikam，如中所述[步骤 7： 配置 MDN 发送端口](../core/step-7-configure-the-mdn-send-port.md)。  
  
## <a name="see-also"></a>请参阅  
 [BizTalk Server 如何接收 AS2 消息](../core/how-biztalk-server-receives-as2-messages.md)   
 [配置 AS2 消息的接收端口](../core/configuring-a-receive-port-for-messages-over-as2.md)