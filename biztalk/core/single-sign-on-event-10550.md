---
title: 单一登录： 事件 10550 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73d63bc5-1e60-426c-a0d6-55c51dbb8d76
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 987e01d741ef49245c931f828f6cebeb3bf52cd2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021955"
---
# <a name="single-sign-on-event-10550"></a>单一登录： 事件 10550
## <a name="details"></a>详细信息  
  
|                 |                                                                                                                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  产品名称   |                                                                                           企业单一登录                                                                                           |
| 产品版本 |                                                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                           |
|    事件 ID     |                                                                                                     10550                                                                                                     |
|  事件源   |                                                                                                    ENTSSO                                                                                                     |
|    组件    |                                                                                                      N/A                                                                                                      |
|  符号名称  |                                                                                        SSO_ERROR_SERVICE_NOT_SSO_ADMIN                                                                                        |
|  消息正文   | SSO 服务无法启动，因为运行该服务的服务帐户不是 SSO 管理员帐户的成员。%r<br /><br /> SSO Administrators: %1 %r<br /><br /> SSO 服务帐户： %2 |
  
## <a name="explanation"></a>解释  
 SSO 服务必须是 SSO 管理员帐户的成员的服务帐户下运行。  
  
## <a name="user-action"></a>用户操作  
 有关详细信息，请参阅[如何指定 SSO Administrators 和 Affiliate Administrators 帐户](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md)。