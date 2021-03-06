---
title: JD Edwards EnterpriseOne 架构导入到 Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 640d5884-953a-46b6-b9dc-b931392a3059
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ffc55fcb2bf5dd563dcc0fc9e2aed93b3a0c624
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009566"
---
# <a name="importing-schemas-into-biztalk-server-projects"></a>架构导入到 BizTalk Server 项目
本部分讨论浏览 JD Edwards EnterpriseOne 服务器和将架构导入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 项目中。  
  
> [!NOTE]
>  您必须确保已设置 arglist。 在业务流程中生成架构之前，您必须更新 jdearglist.txt。 有关详细信息，请参阅[处理字符串值](../core/handling-string-values2.md)。  
  
> [!NOTE]
>  每次更改 jdearglist 时，都必须为该业务对象重新生成架构。  
  
 在创建 JD Edwards EnterpriseOne 端口后，可以通过从 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 项目中启动 Microsoft 适配器向导来浏览 JD Edwards EnterpriseOne。  
  
## <a name="import-schemas-into-visual-studio"></a>架构导入到 Visual Studio
  
1. 打开 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
2. 右键单击名称[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]项目，指向**添加**，然后选择**添加生成的项**。  
  
3. 单击**外**以打开**添加适配器向导**。  
  
4. 上**选择适配器**页上，选择你想要导入架构的适配器的名称 (例如， **JDEEnterpriseOne**)。  
  
5. 在中**SQL Server**框中，选择一个 SQL server。  
  
6. 在中**数据库**框中，选择一个数据库。  
  
    默认数据库与 SQL 服务器相同。  
  
7. 在中**端口**框中，选择一个 SQL server，，然后单击**下一步**。  
  
    浏览器中将显示 JD Edwards EnterpriseOne 系统。  
  
8. 继续执行下一个过程。  
  
   添加适配器向导将显示所有已定义系统的树视图。 JD Edwards EnterpriseOne 具有许多模块。 这些模块根据其名称的前三个字符组合在一起。  
  
- 层次结构的第一层是该模块名称所有三个字符前缀的列表。  
  
- 第二层列出所有共享相同三字符前缀的模块。  
  
- 最后一层列出属于某个模块的业务功能。 当您展开服务图标时，便可以查看其操作。  
  
  展开某项操作后，将显示输入/输出参数。 您可以展开输入/输出参数以查看该参数的数据类型。  
  
> [!NOTE]
>  如果服务器对象定义发生更改，您必须重新生成架构以刷新其包含的数据。  
  
> [!NOTE]
>  如果您在生成架构后更改了 jdearglist.txt，则必须重新生成架构以刷新其包含的数据。 有关 jdearglist.txt 的详细信息，请参阅[处理字符串值](../core/handling-string-values2.md)。  
  
## <a name="select-the-schemas"></a>选择架构  
  
1. 在中**选择导入的服务**页上，展开的顶级节点**业务对象**节点或**业务服务**节点。  
  
2. 选择你想要导入，然后单击项旁边的复选框**确定**。  
  
3. 为选定 JD Edwards EnterpriseOne 项目生成的架构将会导入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 项目中。  
  
> [!NOTE]
>  使用 AddressBook (N0100041) 时的字段名称是**cActionCode**。 此操作是 XML 文件自身的一部分。 这些代码为：  
  
-   A 代表添加  
  
-   C 代表更改  
  
-   D 代表删除  
  
-   I 代表查询  
  
## <a name="next-step"></a>下一步
[使用消息上下文属性](../core/using-message-context-properties1.md)