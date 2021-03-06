---
title: 单一登录： 事件 10728 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f579189c-c9a5-4d2c-a3d5-f0ba03c5a3ef
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5e37738d0bf566b2faf3b5b65c1152cd3ef6405
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995286"
---
# <a name="single-sign-on-event-10728"></a>单一登录： 事件 10728
## <a name="details"></a>详细信息  

|                 |                                                                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  产品名称   |                                                                                                                     企业单一登录                                                                                                                     |
| 产品版本 |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                     |
|    事件 ID     |                                                                                                                               10728                                                                                                                               |
|  事件源   |                                                                                                                              ENTSSO                                                                                                                               |
|    组件    |                                                                                                                                N\A                                                                                                                                |
|  符号名称  |                                                                                                                         SSO_ERROR_VERSION                                                                                                                         |
|  消息正文   | 此版本的 SSO 服务器与 SSO 数据库不兼容。 请升级您的主密钥服务器。%r<br /><br /> SQL Server 名称: %1 %r<br /><br /> SSO 数据库名称: %2 %r<br /><br /> SSO 数据库版本: %3 %r<br /><br /> 所需的版本： %4 |

## <a name="explanation"></a>解释  
 此错误事件表示，SSO 服务器版本比（最初创建的版本）SSO 数据库更新。  

## <a name="user-action"></a>用户操作  
 若要解决此错误，请执行以下操作：  

- 升级 SSO 主密钥服务器以匹配此 SSO 服务器的当前版本。 此操作会将 SSO 数据库升级到当前版本。  

  有关详细信息，请参阅下列资源：  

- [管理主密钥](../core/managing-the-master-secret.md)
