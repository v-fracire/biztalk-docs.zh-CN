---
title: 单一登录： 事件 10565 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d279491-dc0d-44c4-a77e-a67498a3481d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d31b639853b845169c3360ec6367aee120a266d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007998"
---
# <a name="single-sign-on-event-10565"></a>单一登录： 事件 10565
## <a name="details"></a>详细信息  
  
|                 |                                                                                                                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  产品名称   |                                                                                           企业单一登录                                                                                           |
| 产品版本 |                                                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                           |
|    事件 ID     |                                                                                                     10565                                                                                                     |
|  事件源   |                                                                                                    ENTSSO                                                                                                     |
|    组件    |                                                                                                      N/A                                                                                                      |
|  符号名称  |                                                                                       SSO_ERROR_SECRET_VALIDATE_FAILED                                                                                        |
|  消息正文   | 无法从注册表加载密钥。 SSO 服务的服务帐户可能已更改或者密钥可能已损坏。 从备份文件还原密钥。%r<br /><br /> MSID: %1 |
  
## <a name="explanation"></a>解释  
 系统中的管理员可能已更改 SSO 服务帐户，因此无法解密。  
  
## <a name="user-action"></a>用户操作  
 查找更改了 SSO 服务帐户的人员，然后从备份文件还原密钥。 还原密钥的详细信息，请参阅[管理主密钥](../core/managing-the-master-secret.md)。