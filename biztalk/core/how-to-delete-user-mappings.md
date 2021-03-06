---
title: 如何删除用户映射 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps [SSO], deleting
- managing [SSO maps], deleting user maps
ms.assetid: de511113-b0b0-4920-91dc-4c9e380fda58
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 034f587d8c7d87f5fa6aa7e5e33ca4ef147d9f9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014382"
---
# <a name="how-to-delete-user-mappings"></a>如何删除用户映射
使用以下命令以删除一个或多个用户映射，按照指定的 XML 文件中。 下面是示例 XML 文件。  
  
```  
<sso>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name1</externalApplication>   
<externalUserId>App1UserName</externalUserId>   
</mapping>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name2</externalApplication>   
<externalUserId>App2UserName</externalUserId>   
</mapping>  
</sso>  
```  
  
 如果用户不是应用程序用户帐户的成员或 Active Directory 中不存在，应使用此命令以从 SSO 数据库中删除用户映射。  
  
 如果更改用户帐户，您必须使用此命令可删除旧的用户映射，，然后创建新用户帐户的新用户映射。 有关创建映射的详细信息，请参阅[如何创建用户映射](../core/how-to-create-user-mappings.md)。  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a>若要删除用户映射使用管理实用工具  
  
1. 上**启动**菜单上，单击**运行**，然后键入**cmd**。  
  
2. 在命令行上，转至企业单一登录安装目录。 默认安装目录\<*驱动器*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 类型<strong>ssomanage-deletemappings *\<映射文件名称\></strong><em>，其中\<</em>映射文件的名称*\>是包含你想要删除用户映射文件的名称。  
  
   > [!NOTE]
   >  在支持用户帐户控制 (UAC) 的系统上，可能需要具有管理权限才能运行该工具。  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a>若要删除特定用户映射使用管理实用工具  
  
1. 上**启动**菜单上，单击**运行**，然后键入**cmd**。  
  
2. 在命令行上，转至企业单一登录安装目录。 默认安装目录*\<驱动器*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 类型 **ssomanage-deletemapping *\<域\>*\\*\<用户名\>*   *\<应用程序名称\>**<em>，其中*\<域\></em>是 Windows 域用户帐户 *\<用户名\>* 是 Windows 用户名，并\<* 应用程序名称*\>是你想要删除其用户映射的特定应用程序。  
  
   > [!NOTE]
   >  在支持用户帐户控制 (UAC) 的系统上，可能需要具有管理权限才能运行该工具。  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a>若要删除使用客户端实用工具的用户映射  
  
1. 上**启动**菜单上，单击**运行**，然后键入**cmd**。  
  
2. 在命令行上，转至企业单一登录安装目录。 默认安装目录*\<驱动器*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 类型 * * ssoclient-deletemapping *\<应用程序名称\>**<em>，其中 *\<应用程序名称\></em>是你想要删除关联应用程序的名称用户映射。  
  
   > [!NOTE]
   >  在支持用户帐户控制 (UAC) 的系统上，可能需要具有管理权限才能运行该工具。  
  
## <a name="see-also"></a>请参阅  
 [SSO 映射](../core/sso-mappings.md)   
 [管理关联应用程序](../core/managing-affiliate-applications.md)   
 [管理用户映射](../core/managing-user-mappings.md)