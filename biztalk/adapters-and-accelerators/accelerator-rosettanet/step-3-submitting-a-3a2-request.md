---
title: 步骤 3： 提交 3A2 请求 |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, submitting requests
ms.assetid: 09f22be8-6d7d-48bf-862b-73248bae0506
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 312e5980636d211f1e023331826e016eb141eb4b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967531"
---
# <a name="step-3-submitting-a-3a2-request"></a>步骤 3： 提交 3A2 请求
在此步骤中，将使用 3A2 - 请求价格与可用性的合作伙伴接口流程 (PIP) 准备并提交请求。 通过此 PIP，买方组织可以获得有关特定产品的信息，如价格和可用单位数。 然后，买方就可以通过业务规则对获得的信息进行处理，以便确定是否购买相应供应商的产品。  
  
### <a name="to-submit-a-3a2---request-price-and-availability"></a>提交 3A2 - 请求价格与可用性  
  
1.  在 Fabrikam 计算机上的 Internet Explorer 中，找到并打开 http://localhost/LOBWebApplication/default.aspx。  
  
2.  上**提交消息**页上，执行以下操作：  
  
    |使用此选项|执行的操作|  
    |--------------|----------------|  
    |**本组织**|类型**FABRIKAM**。|  
    |**伙伴组织**|类型**Contoso**。|  
    |**Pip 代码**|类型**3A2**。 **重要说明：** 若要避免重复的消息 ID 错误，你必须确保**Pip**对于你提交每条消息是唯一的。 如果以后运行 3A2 测试，则必须更改本字段。|  
    |**Pip 版本**|类型**R02.00.00A**。|  
    |**Pip 实例 ID**|类型**3A2_Test**。|  
    |**消息类别**|类型**操作**。|  
  
3.  使用记事本或其他文本编辑器，打开在文件 3A2_Request.xml *\<驱动器\>*: \程序 Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances 文件夹，然后复制并粘贴到的内容**服务内容**字段LOBWebApplication。  
  
4.  单击**提交**以提交到 Contoso 计算机 3A2 请求。  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a>检验 Fabrikam 计算机上的通信是否成功  
  
-   上**消息状态**LOBWebApplication 在页上，请验证是否接收两个传入消息。  
  
    > [!NOTE]
    >  首先应收到一条类别为 25 的消息，该消息为 Contoso 计算机的确认回执。 然后，应收到一条类别为 50 的消息，该消息为 Contoso 计算机的响应消息。 类别为 -99 的消息表示发生错误。 你可以使用**事件查看器**以确定实际错误消息。  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a>检验 Contoso 计算机上的通信是否成功  
  
1.  单击**启动**，指向**所有程序**，指向**Microsoft SQL Server 2008 R2**，然后单击**SQL Server Management Studio**。  
  
2.  在**连接到服务器**对话框中，在**SQL Server**框中，键入**localhost**，选择**Windows 身份验证**，然后单击**连接**。  
  
3.  在 Microsoft SQL Server Management Studio 中，单击**新查询**。  
  
4.  在\<表\>文本框中，选择**BTARNDATA**从列表中。  
  
5.  在“SQL”窗口中，键入以下 SQL 语句：  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  单击**执行**运行 SQL 语句。  
  
7.  在“查询”窗口的“结果”窗格中，检验你是否看到两条传入消息。  
  
    > [!NOTE]
    >  首先应收到一条类别为 10 的消息，该消息代表 Fabrikam 计算机发送的原始请求。 然后，应收到一条类别为 25 的消息，该消息为确认消息回执。  
  
8.  在“SQL”窗口中，键入以下 SQL 语句：  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. 单击**执行**运行 SQL 语句。  
  
10. 在“查询”窗口的“结果”窗格中，检验你是否看到一条传出消息。  
  
    > [!NOTE]
    >  应看到类别为 25 的消息，该消息代表从 Contoso 计算机发送到 Fabrikam 计算机的确认回执。 还应看到类别为 50 的消息，该消息代表从 Contoso 业务线 (LOB) 应用程序发送到 Fabrikam 计算机的响应。  
  
## <a name="see-also"></a>另请参阅  
 [步骤 4： 提交 3A4 请求](../../adapters-and-accelerators/accelerator-rosettanet/step-4-submitting-a-3a4-request.md)   
 [BTARN 中的消息流](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)