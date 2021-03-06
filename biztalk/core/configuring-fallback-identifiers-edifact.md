---
title: 配置回退标识符 (EDIFACT) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2ce56c1-44f1-42dc-94e8-36e5ba664f53
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7db7e20f8ccb4db8da53483e7c33285f4b75afb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991982"
---
# <a name="configuring-fallback-identifiers-edifact"></a>配置回退标识符 (EDIFACT)
在后备协议中，必须设置收件人引用密码，以确认交换不会被未经授权的收件人接收。  
  
## <a name="prerequisites"></a>必要條件  
 必须以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理员组或 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators 组成员的身份登录。  
  
### <a name="to-set-the-sender-recipient-recipient-password"></a>设置发件人、收件人、收件人密码  
  
1. 在中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理控制台中，右键单击**方**节点，，然后单击**EDIFACT 后备设置**。  
  
2. 在中**EDIFACT 后备设置**对话框中**EDIFACT 协议页**选项卡上，在**交换设置**部分中，单击**标识符**.  
  
3. 在中**发件人 (UNB2)** 部分中，执行以下操作：  
  
   1.  有关**标识 (UNB2.1)**，输入一个最小值和最多为 35 的字母数字值。 这是必填字段。  
  
   2.  有关**代码限定符 (UNB2.2)**，从下拉列表中选择一个值。 此字段为可选字段。  
  
   3.  有关**反向路由地址 (UNB2.3)**，输入包含最少一个字符，最多为 14 个字符的字母数字值。 此字段为可选字段。  
  
   4.  有关**应用程序引用 ID (UNB7)**，输入包含最少一个字符，最多为 6 个字符的字母数字值。 这是必填字段。  
  
4. 在中**收件人 (UNB3)** 部分中，执行以下操作：  
  
   1.  有关**标识 (UNB3.1)**，输入一个最小值和最多为 35 的字母数字值。 这是必填字段。  
  
   2.  有关**代码限定符 (UNB3.2)**，从下拉列表中选择一个值。 此字段为可选字段。  
  
   3.  有关**反向路由地址 (UNB3.3)**，输入包含最少一个字符，最多为 14 个字符的字母数字值。 此字段为可选字段。  
  
   4.  如果需要，在**收件人引用密码 (UNB6)** 部分中，输入收件人引用密码的值。 有关**值 (UNB6.1)**，输入一个最小值和最多 14 个字母数字值。 有关**限定符 (UNB6.2)**，输入包含最少一个字符，最多两个字符的字母数字值。 这些是可选字段。 如果这些值与所接收交换中的 UNB6.1 和 UNB6.2 字段不匹配，BizTalk Server 将挂起该交换。  
  
       > [!NOTE]
       >  组合**UNB6.1**并**UNB6.2**必须是唯一的。  
  
       > [!NOTE]
       >  如果同时为 UNB6.1 和 UNB6.2 输入值，应用更改，然后取消 UNB6.1，则 UNB6.2 中的值也将被删除，而且该字段将被禁用。  
  
5. 单击**Apply**以接受更改，然后才能继续进行配置，或单击**确定**以验证所做的更改，然后关闭对话框。  
  
## <a name="see-also"></a>请参阅  
 [为交换处理配置 EDIFACT 后备协议属性](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)