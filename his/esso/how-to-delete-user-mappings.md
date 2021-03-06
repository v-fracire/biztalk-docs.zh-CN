---
title: 如何删除用户映射 |Microsoft 文档
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c4cdff-b82d-4cfd-8e20-220a2fe78656
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: a9d0a31c3dbc9d5980f59d9f30d20ec15f603a38
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2018
ms.locfileid: "30251081"
---
# <a name="how-to-delete-user-mappings"></a>如何删除用户映射
使用这些命令来删除一个或多个用户映射，按照指定的 XML 文件中。 下面是示例 XML 文件。  
  
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
  
 如果用户不是 Application Users 帐户的成员或 Active Directory 中不存在，你应使用此命令从凭据数据库中删除的用户映射。  
  
 如果更改用户帐户，你必须使用此命令删除的旧的用户映射，然后创建新的用户帐户的新用户映射。 有关创建一个映射的详细信息，请参阅[如何创建用户映射](../esso/how-to-create-user-mappings.md)。  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a>若要删除使用管理实用程序的用户映射  
  
1.  单击 **启动**, ，单击 **运行**, ，类型 `cmd`, ，然后按 ENTER。  
  
2.  在命令提示符处，转到企业单一登录安装目录。  
  
     默认安装目录是\<*驱动器*>: \program Files\Enterprise 单一登录。  
  
3.  类型`ssomanage –deletemappings <mappings file name>`，其中\<*映射文件名*> 是包含你想要删除的用户映射的文件的名称。  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a>若要删除特定用户映射使用管理实用工具  
  
1.  单击 **启动**, ，单击 **运行**, ，类型 `cmd`, ，然后按 ENTER。  
  
2.  在命令提示符处，转到企业单一登录安装目录。  
  
     默认安装目录是*\<驱动器 >*: \program Files\Enterprise 单一登录。  
  
3.  类型`ssomanage –deletemapping <domain>\<username> <application name>`，其中*\<域 >* 是用户帐户的 Windows 域*\<用户名 >* 是 Windows 用户名称，并\< *应用程序名称*> 是你想要删除的用户映射的特定应用程序。  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a>若要删除使用客户端实用工具的用户映射  
  
1.  单击 **启动**, ，单击 **运行**, ，类型 `cmd`, ，然后按 ENTER。  
  
2.  在命令提示符处，转到企业单一登录安装目录。  
  
     默认安装目录是*\<驱动器 >*: \program Files\Enterprise 单一登录。  
  
3.  类型`ssoclient –deletemapping <application name>`，其中*\<应用程序名称 >* 是你想要删除的用户映射的关联应用程序的名称。  
  
## <a name="see-also"></a>另请参阅  
 [SSO 映射](../esso/sso-mappings.md)   
 [管理关联应用程序](../esso/managing-affiliate-applications.md)   
 [管理用户映射](../esso/managing-user-mappings.md)