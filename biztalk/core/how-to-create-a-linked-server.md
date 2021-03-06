---
title: 如何创建链接的服务器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- servers, linking for backups
- backing up, linking servers
ms.assetid: 7d4aba3d-77c0-4cdf-8547-71e821ce34a1
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcb954062bb2cb2484a51570109b37341b1c12f9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980982"
---
# <a name="how-to-create-a-linked-server"></a>如何创建链接服务器
当 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安装在分布式拓扑中时，多个 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 上均存在属于 BizTalk 组的数据库。 在能够从 BizTalk 管理服务器备份整个 BizTalk 环境之前，必须配置到每个远程服务器的链接服务器连接。 链接服务器是 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 分布式查询中使用的 OLE DB 数据源。  
  
 在备份和还原过程中，备份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 作业将自动创建链接服务器。 不过，如果需要，您可通过以下过程手动创建链接服务器。  
  
 此外可以使用创建链接的服务器*sp_addlinkedserver*存储过程。 执行此操作时，须注意以下安全事项。 在使用 sp_addlinkedserver 创建链接服务器时，所有本地登录都将默认映射到新的链接服务器。 若要控制对链接服务器的访问*sp_droplinkedsvrlogin*过程应该用于删除全局登录映射后, 跟*sp_addlinkedsvrlogin*将映射到的所需的登录帐户新建链接的服务器。 在使用 sp_addlinkedsvrlogin 时，建议您设置@useself参数 = TRUE。 这样就无需将用户名和密码嵌入到您的 SQL 脚本中。  

> [!TIP]
> 这些步骤可能随时间变化。 我们建议引用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]文档，网址[创建链接服务器](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine)。
  
## <a name="prerequisites"></a>必要條件  
  
- 是的成员的帐户登录[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] **sysadmin**固定的服务器角色  
  
- 创建本地[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]登录名。 在以下步骤中，此帐户映射到登录名在[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，将链接到。 
  
## <a name="create-a-linked-server"></a>创建链接的服务器
  
1. 打开**SQL Server Management Studio**，输入你的本地名称[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，然后选择**Connect**。  
  
2. 展开**Server 对象**，右键单击**链接服务器**，然后选择**新建链接服务器**。  

   若要查看**Server 对象**，连接到本地内部[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 然后， **Server 对象**应显示。
  
3. 在中**链接服务器**文字框中，输入的完整网络名称[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]你想要链接到。  
  
   > [!NOTE]
   >  此过程通常针对的是要链接到的作为远程服务器的服务器。 这只是为了方便，用以指示链接（“远程”）服务器与本地服务器的关系。  
  
4. 下**服务器类型**，选择**SQL Server**。  
  
5. 在左窗格中，选择“安全性” 。 

   在此步骤中，你创建的本地帐户映射到远程服务器登录名。 选项包括： 
    
   | | | 
   |---|---|
   | **可使用登录名的当前安全上下文** | 在域环境中，用户通常使用其域登录名连接。 由于登录的域帐户的安全上下文映射到你创建的本地帐户，此选项可能是最佳。|
   | **使用此安全上下文建立连接** | 当用户连接到本地 SQL Server 使用 SQL Server 登录名时，则此选项可能是最佳。 然后输入登录名和密码的帐户链接的服务器上。 |


6. 选择**添加**，并输入以下命令： 

   1. 下**本地登录名**，选择你创建的本地帐户。 
   2. 检查**Impersonate**如果远程服务器上还存在本地登录名。 
   3. 或者，如果将本地登录名映射到远程[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]登录名，输入**远程用户**名称并**远程密码**的远程服务器登录名。  
  
      > [!NOTE]
      >  若要使用模拟，则您的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 配置和登录帐户必须满足委派要求。 请参阅[委派配置链接服务器](https://msdn.microsoft.com/library/ms189580.aspx)的更多详细信息。  

7. 在左窗格中，选择**服务器选项**。 设置**RPC**并**RPC Out**参数**True**，然后选择**确定**。 
 
> [!TIP]
> 有关详细信息和建议创建链接的服务器时使用 includig`sp_addlinkedserver`存储 procedcure，请参阅[创建链接服务器](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine)。

  
## <a name="see-also"></a>请参阅  
 [有关备份和还原的高级信息](../core/advanced-information-about-backup-and-restore1.md)