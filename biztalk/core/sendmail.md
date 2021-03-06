---
title: SendMail |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SMTP adapters, examples
- examples, SMTP adapters
- SMTP adapters
ms.assetid: a0258619-b195-4c8a-8326-77add6e6f04d
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca2b9f3be3fd54d34cec1bdfadda723a42f3b6c7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005678"
---
# <a name="sendmail"></a>SendMail
SendMail 示例演示如何使用简单邮件传输协议 (SMTP) 适配器在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 业务流程内发送电子邮件。 用于发送电子邮件的动态信息是通过使用属性升级功能从 XML 消息中检索得到的。  

## <a name="what-this-sample-does"></a>本示例的用途  
 本示例使用升级自传入 XML 采购订单 (PO) 消息的属性中的信息来发送电子邮件，其具体的操作步骤如下所示：  

1. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 业务流程检索输入的 XML PO 消息。  

2. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]业务流程升级**PONumber**并**电子邮件**以便于将来访问的属性。  

3. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 业务流程使用升级属性的值设置动态发送端口的目标地址和电子邮件的主题。  

4. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 业务流程通过 SMTP 适配器发送构造好的电子邮件。  

## <a name="where-to-find-this-sample"></a>本示例所在的位置  
 \<*示例路径*\>\AdaptersUsage\SendMail\  

 下表显示了本示例中的文件及其用途说明：  


|                    文件                     |                                                                                                         Description                                                                                                         |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AssemblyInfo.cs、SendMail.btproj、SendMail.sln |                                                                         提供本示例的项目、解决方案和程序集信息文件。                                                                         |
|                  Cleanup.bat                   |              取消部署程序集并将其从全局程序集缓存 (GAC) 中删除；删除发送和接收端口；根据需要删除 Microsoft Internet 信息服务 (IIS) 虚拟目录。               |
|     PropertySchema.xsd、PurchaseOrder.xsd      |                                                           分别为要升级的属性和 XML PO 消息提供架构。                                                           |
|                ReceiveSend.odx                 |   提供用于处理传入 XML PO 消息并根据消息中的信息发送电子邮件的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 业务流程。   |
|               SendMailInput.xml                |                                                                                 包含具有使用 XML 指定的 PO 的示例输入文件。                                                                                 |
|                   Setup.bat                    | 生成并初始化本示例。 **注意：** 此安装程序文件创建并绑定端口，和在其他方面，使用不同的机制与绝大多数安装程序文件，以 SDK 示例。 它不需要 companion .xml 文件。 |

### <a name="to-build-and-initialize-this-sample"></a>构建和初始化此示例  

1. 在命令窗口中，导航到下面的文件夹：  

    \<*示例路径*\>\AdaptersUsage\SendMail  

2. 运行 Setup.bat 文件，该文件将执行以下操作：  

   - 为本示例创建以下输入文件夹：  

      \<*示例路径*\>\AdaptersUsage\SendMail\In  

   - 编译[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]此示例项目。  

   - 启动 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 业务流程。  

     > [!NOTE]
     >  在尝试运行本示例之前，应确认在生成和初始化过程中 BizTalk 未报告任何错误。  

     > [!NOTE]
     >  如果选择在不运行 Setup.bat 文件的情况下打开并生成本示例中的项目，则必须首先使用 .NET Framework 强名称实用工具 (sn.exe) 创建一个强名称密钥对。 使用此密钥对生成程序集进行签名。  

     > [!NOTE]
     >  若要撤消 Setup.bat 所做的更改，请运行 Cleanup.bat，并删除所有接收和发送前缀为 SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail 的端口。 必须运行 Setup.bat 前运行 Cleanup.bat 时间。  

3. 在中**BizTalk Server 管理**控制台中，找到前缀为 SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail 的接收端口。 更新此接收端口，以指向您要用作输入位置的文件系统上的目录的接收位置。  

4. 使用程序 （如记事本） 修改 SendMailInput.xml 文件，以便**电子邮件**元素指定想要接收电子邮件，此示例生成一个合法的电子邮件地址。  

5. 单击**启动**，依次指向**程序**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然后单击**BizTalk Server 管理**。  

6. 在中**BizTalk Server 管理**控制台中，展开 BizTalk 组树。  

7. 展开**平台设置**树中的左窗格中。  

8. 展开**适配器**文件夹中，单击**SMTP**节点，然后再双击右侧窗格中的 SMTP 适配器行。  

9. 在中**SMTP-适配器处理程序属性**对话框中，单击**属性**。  

10. 在中**SMTP 传输属性**对话框中，在**属性**选项卡上，提供相应的值**SMTP 服务器名称**和**从 （电子邮件地址）** 属性，并单击**确定**。  

     这些值将用于构造通过此 SMTP 适配器发送任何电子邮件的 From 电子邮件地址。  

    > [!NOTE]
    >  如果你需要使用你的 SMTP 服务器进行身份验证，则必须确保 From 电子邮件地址属于同一个帐户的使用进行身份验证。  

11. 停止，然后重新启动 BizTalk 服务 (BizTalkServerApplication)，以使业务流程将采用这些更改。  

### <a name="to-run-this-sample"></a>运行本示例的步骤  

1.  将修改的 SendMailInput.xml 文件的副本放到输入文件夹下。  

2.  观察到在上一步骤中指定的电子邮件地址的电子邮件到达。  

## <a name="see-also"></a>请参阅  
 [适配器示例 - 用法](../core/adapter-samples-usage.md)