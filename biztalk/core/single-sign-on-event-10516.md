---
title: 单一登录： 事件 10516 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d20df92f-c995-4cbc-a8f9-21cea30b82c9
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d0f3ab8e5d368c04b1a93b9e7e00efa76c50283
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023523"
---
# <a name="single-sign-on-event-10516"></a>单一登录： 事件 10516
## <a name="details"></a>详细信息  

|                 |                                                                                                                                                                                                                                                                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  产品名称   |                                                                                                                                                            企业单一登录                                                                                                                                                            |
| 产品版本 |                                                                                                                                           [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                            |
|    事件 ID     |                                                                                                                                                                      10516                                                                                                                                                                      |
|  事件源   |                                                                                                                                                                     ENTSSO                                                                                                                                                                      |
|    组件    |                                                                                                                                                                       N\A                                                                                                                                                                       |
|  符号名称  |                                                                                                                                                           SSO_ERROR_BAD_SSO_APP_ADMIN                                                                                                                                                           |
|  消息正文   | SSO 关联管理员帐户无效。 如果是本地帐户，请检查服务器上是否存在此帐户。 如果是域帐户，请与域管理员联系。 当帐户有效时，启用 SSO。%r<br /><br /> SSO 关联管理员: %1 %r<br /><br /> 无效帐户: %2 %r<br /><br /> 错误代码： %3 |

## <a name="explanation"></a>解释  
 此错误事件表示，企业单一登录创建的 SSO 关联管理员帐户或组不是有效的 Windows 帐户。 SSO 关联管理员帐户可以是 Windows 组帐户或个人帐户。 SSO 关联管理员帐户也可以是域或本地组帐户。  

## <a name="user-action"></a>用户操作  
 若要解决此错误，请执行以下操作：  

- 验证 SSO 关联管理员帐户是否存在。  

  有关详细信息，请参阅 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 帮助中的以下资源：  

- [SSO 用户组](../core/sso-user-groups.md)  

- [如何更新 SSO 数据库](../core/how-to-update-the-sso-database.md)
