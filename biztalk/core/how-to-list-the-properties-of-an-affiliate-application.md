---
title: 如何列出关联应用程序的属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], listing properties
- managing [SSO applications], listing properties
ms.assetid: a120acd7-2f0b-4c72-8a8a-f8e500a773c8
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5920263006a9188da83f82dcf65dad8fb8faada
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002718"
---
# <a name="how-to-list-the-properties-of-an-affiliate-application"></a>如何列出关联应用程序的属性
此命令显示有关关联应用程序的以下信息。 有关关联应用程序的属性的详细信息，请参阅[SSO 关联应用程序](../core/sso-affiliate-applications.md)。  
  
 SSO 系统从用于更新关联应用程序的 xml 文件获取这些信息。 有关详细信息，请参阅[如何更新关联应用程序的属性](../core/how-to-update-the-properties-of-an-affiliate-application.md)。  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-administration-utility"></a>使用管理实用工具显示关联应用程序的属性  
  
1. 上**启动**菜单上，单击**运行**，然后键入**cmd**。  
  
2. 在命令行上，转至企业单一登录安装目录。 默认安装目录\<*驱动器*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 类型 * * ssomanage-displayapp *\<应用程序名称\>**<em>，其中 *\<应用程序名称\></em>是你想要显示的关联应用程序的名称属性。  
  
   > [!NOTE]
   >  在支持用户帐户控制 (UAC) 的系统上，可能需要具有管理权限才能运行该工具。  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-client-utility"></a>使用客户端实用工具显示关联应用程序的属性  
  
1. 上**启动**菜单上，单击**运行**，然后键入**cmd**。  
  
2. 在命令行上，转至企业单一登录安装目录。 默认安装目录\<*安装驱动器*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 类型 * * ssoclient-displayapp *\<应用程序名称\>**<em>，其中 *\<应用程序名称\></em>是你想要显示的关联应用程序的名称属性。  
  
   > [!NOTE]
   >  在支持用户帐户控制 (UAC) 的系统上，可能需要具有管理权限才能运行该工具。  
  
## <a name="see-also"></a>请参阅  
 [管理用户映射](../core/managing-user-mappings.md)   
 [管理关联应用程序](../core/managing-affiliate-applications.md)