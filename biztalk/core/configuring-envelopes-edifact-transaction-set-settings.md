---
title: 配置信封 （EDIFACT 事务集设置） |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec140def-6155-4b8a-8489-6e0a530bd697
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a1d910f52d9ea90ae0c486356a7ecb3b01bf07a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234629"
---
# <a name="configuring-envelopes-edifact-transaction-set-settings"></a>配置信封（EDIFACT--事务集设置）
在**包络线**页**事务设置设置**部分中，你定义如何 BizTalk Server 生成的 UNG 段和新罕布什尔大学段它将发送到方的 EDIFACT 编码交换。  
  
 UNG 段是用来标识和指定 EDIFACT 编码交换的功能组的标头。 它包含有关准备功能组的日期和时间以及功能组中文档的类型和版本的信息。  
  
 UNH 段是 EDIFACT 编码的交换的消息标头段。 UNH 段提供了有关消息类型以及负责维护该消息类型发布的机构的信息。 该段指示交换中文档的开头以及后面文档的类型。  
  
 在**功能组标头 (UNG)** 部分中，你将关联**UNG**值与**新罕布什尔大学**值和命名空间。 BizTalk Server 确定 BizTalk XML 消息已设置的值**新罕布什尔大学**元素和**目标命名空间**在网格的行中，BizTalk 服务器将填充**UNG**同一行的网格中的值的数据元素。 值**新罕布什尔大学**元素和**目标命名空间**必须是唯一的。  
  
 如果消息没有包含的匹配项**新罕布什尔大学**元素和**目标命名空间**在任何行中，BizTalk Server 将填充的值的消息**UNG**默认行中的元素。 将使用这些值，即使消息不具有与匹配**新罕布什尔大学**元素和**目标命名空间**的默认行。  
  
 当 BizTalk 引擎确定 BizTalk XML 消息具有新罕布什尔大学元素和目标命名空间设置的值时，引擎会使用为其设置在网格中，提供的值填充 UNG 元素在消息中的**创建分组段**选中复选框。  
  
> [!NOTE]
>  在**功能组标头 (UNG)** 部分中，如果你在网格中，输入的任何字段的设置，然后删除该设置，您将需要删除整行或页将未通过验证。  
  
> [!IMPORTANT]
>  所有属性上将都禁用**A 方-> 方 B**单向协议选项卡，如果你清除**本地 BizTalk 处理接收方或支持从该参与方发送消息的消息**检查框 a 方。但是，在中相同页面上启用的所有属性**B 方-> A 方**选项卡上，如果创建 a 方。 时选中复选框  
  
## <a name="prerequisites"></a>先决条件  
 必须以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理员组或 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators 组成员的身份登录。  
  
### <a name="to-define-the-ung-and-unh-segments"></a>若要定义的段 UNG 和新罕布什尔大学段  
  
1.  创建 EDIFACT 编码协议中所述[配置常规设置 (EDIFACT)](../core/configuring-general-settings-edifact.md)。 若要更新现有协议，右键单击在协议**方和业务配置文件**页，然后单击**属性**。  
  
2.  单向协议选项卡上，在**事务设置设置**部分中，单击**包络线**。  
  
3.  在网格的某行中，输入以下值：  
  
    -   在**消息键入 UNH2.1**列中，输入事务集类型。 （最长不得超过 6 个字符）。  
  
    -   在**UNH2.2**列中，输入消息版本号。 （最小长度为 1 个字符；最大长度为 3 个字符）。  
  
    -   在**UNH2.3**列中，输入消息发行版号。 （最小长度为 1 个字符；最大长度为 3 个字符）。  
  
    -   在**UNH2.5**列中，输入所分配的代码。 （最长不得超过 6 个字符。 必须为字母数字值）。  
  
    -   在**目标命名空间**列中，选择架构的目标命名空间。 这是必填字段。  
  
        > [!NOTE]
        >  BizTalk Server 会将这些值与它所生成的交换的关联值进行比较。  
  
4.  在网格的同一行中，输入以下值：  
  
    -   有关**UNG1** （功能组标识），输入一个字母数字值，该值最少包含一个字符，最多六个字符。 这是必填字段。  
  
    -   有关**UNG2.1** （应用程序发件人标识），输入一个字母数字值，该值最少包含一个字符，最多 35 个字符。 这是必填字段。  
  
    -   有关**UNG2.2** （应用程序发件人代码限定符），输入一个字母数字值，最多四个字符。 此字段为可选字段。  
  
    -   有关**UNG3.1** （应用程序收件人标识），输入一个字母数字值，该值最少包含一个字符，最多 35 个字符。 这是必填字段。  
  
    -   有关**UNG3.2** （应用程序收件人代码限定符），输入一个字母数字值，最多四个字符。 此字段为可选字段。  
  
    -   有关**UNG6** （控制机构），输入一个最小值和最多两个字母数字值。 这是必填字段。  
  
    -   有关**UNG7.1** （消息类型版本号），输入一个字母数字值，该值最少包含一个字符，最多三个字符。 这是必填字段。  
  
    -   有关**UNG7.2** （消息类型发行版号），输入一个字母数字值，该值最少包含一个字符，最多三个字符。 这是必填字段。  
  
    -   有关**UNG7.3** （关联分配代码），输入一个字母数字值，该值最少包含 1 个字符，最多 6 个字符。 这是必填字段。  
  
    -   有关**UNG8** （应用程序密码），输入一个字母数字值，该值最少包含一个字符，最多包含 14 个字符。 这是必填字段。  
  
        > [!NOTE]
        >  这些将是 BizTalk Server 将在生成如果该交换 UNG 字段中输入的值**消息键入 UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**目标命名空间**同一行中的元素是交换关联的匹配项。  
  
5.  重复步骤 4 和 5 网格中输入附加行。  
  
6.  对于在网格中的一个行，请单击**默认**以将其指定为默认行。  
  
    > [!NOTE]
    >  如果消息没有包含的匹配项**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**目标命名空间**任何行，BizTalk Server 中的元素将填充的值的消息**UNG1**， **UNG2.1**， **UNG2.2**， **UNG3.1**， **UNG3.2**， **UNG6**， **UNG7.1**， **UNG7.2**， **UNG7.3**，和**UNG8**默认行中的元素。 将使用这些值，即使消息不具有与匹配**消息键入 UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**目标命名空间**默认行的元素。  
  
    > [!NOTE]
    >  如果选择没有默认行，并且邮件未包含的匹配项**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**目标命名空间**在任何行中，BizTalk 的元素将会挂起消息。  
  
7.  单击**应用**接受所做的更改，然后才能继续进行配置，或单击**确定**验证所做的更改，然后关闭对话框。  
  
## <a name="see-also"></a>另请参阅  
 [配置事务集设置 (EDIFACT)](../core/configuring-transaction-set-settings-edifact.md)