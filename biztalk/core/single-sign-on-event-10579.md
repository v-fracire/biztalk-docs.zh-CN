---
title: 单一登录： 事件 10579 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e18f6d-9dda-49bf-a901-bb28f4cd9a84
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aab40dded4fc677d86c9c1a4ab21d17434cfa8b9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002678"
---
# <a name="single-sign-on-event-10579"></a>单一登录： 事件 10579
## <a name="details"></a>详细信息  
  
|                 |                                                                                                                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  产品名称   |                                                                                                          企业单一登录                                                                                                           |
| 产品版本 |                                                                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                          |
|    事件 ID     |                                                                                                                    10579                                                                                                                     |
|  事件源   |                                                                                                                    ENTSSO                                                                                                                    |
|    组件    |                                                                                                                     N/A                                                                                                                      |
|  符号名称  |                                                                                                       SSO_INFO_CHANGED_APP_ADMIN_GROUP                                                                                                       |
|  消息正文   | 已更新应用程序管理员帐户。%r<br /><br /> 新的 Application Administrators: %1 %r<br /><br /> 旧的 Application Administrators: %2 %r<br /><br /> 跟踪 ID: %3 %r<br /><br /> 客户端用户: %4 %r<br /><br /> 应用程序名称： %5 |
  
## <a name="explanation"></a>解释  
 这是信息性消息，可以用于跟踪 SSO 系统中发生的与安全有关的重要事件。 此消息表明应用程序管理员帐户已经更新。  
  
## <a name="user-action"></a>用户操作  
 不需要任何用户操作。