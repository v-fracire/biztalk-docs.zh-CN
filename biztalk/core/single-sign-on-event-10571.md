---
title: 单一登录： 事件 10571 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c590a00-b8c5-41b4-abb3-0a424e8b052d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 638e04802b2d2cbf4b8089616ac29e451291b5d7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009838"
---
# <a name="single-sign-on-event-10571"></a>单一登录： 事件 10571
## <a name="details"></a>详细信息  
  
|                 |                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  产品名称   |                                                                                          企业单一登录                                                                                           |
| 产品版本 |                                                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                          |
|    事件 ID     |                                                                                                    10571                                                                                                     |
|  事件源   |                                                                                                    ENTSSO                                                                                                    |
|    组件    |                                                                                                     N/A                                                                                                      |
|  符号名称  |                                                                                      SSO_WARN_SSO_NOT_IN_NEW_SSO_ADMIN                                                                                       |
|  消息正文   | 要更改 SSO 管理员帐户名，则 SSO 服务帐户必须是新 SSO 管理员帐户的成员。%r<br /><br /> SSO 服务帐户: %1 %r<br /><br /> 新的 SSO Administrators: %2 |
  
## <a name="explanation"></a>解释  
 要更改 SSO 管理员帐户名，则 SSO 服务帐户必须是新 SSO 管理员帐户的成员。  
  
## <a name="user-action"></a>用户操作  
 角色和帐户的详细信息，请参阅[SSO 用户组](../core/sso-user-groups.md)。