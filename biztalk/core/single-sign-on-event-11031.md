---
title: 单一登录： 事件 11031 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ecd24c2-e251-4eb9-b3ca-ec0f095bb23a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f90be8f631bbd9503de3401bc84d27af32aa991a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015078"
---
# <a name="single-sign-on-event-11031"></a>单一登录： 事件 11031
## <a name="details"></a>详细信息  
  
|                 |                                                                                                                                                                                                                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  产品名称   |                                                                                                                                企业单一登录                                                                                                                                |
| 产品版本 |                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                |
|    事件 ID     |                                                                                                                                          11031                                                                                                                                          |
|  事件源   |                                                                                                                                         ENTSSO                                                                                                                                          |
|    组件    |                                                                                                                                           N/A                                                                                                                                           |
|  符号名称  |                                                                                                                         SSO_INFO_PS_WIN_CHANGE_INVALID_MAPPING                                                                                                                          |
|  消息正文   | Windows 密码更改。 已检测到此 Windows 帐户的映射，但此映射由于不再有效而被忽略。%r<br /><br /> 跟踪 ID: %1 %r<br /><br /> Windows 帐户: %2 %r<br /><br /> 应用程序: %3 %r<br /><br /> 外部帐户: %4 %r<br /><br /> 客户端用户： %5 |
  
## <a name="explanation"></a>解释  
 可能是因为 Windows 帐户存在且有效，但不在应用程序用户帐户中。  
  
## <a name="user-action"></a>用户操作  
 删除映射，然后尝试重新创建该映射。