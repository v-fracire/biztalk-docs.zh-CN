---
title: AS2 解码器无法定位处置通知选项 HTTP 标头 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6de4b9a6-17b2-4455-9dbd-a6bb69fac1d5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 230f0a03e1274fec7ef196ce12cc3be33ff2702b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004558"
---
# <a name="the-as2-decoder-was-unable-to-locate-the-disposition-notification-options-http-header"></a>AS2 解码器无法定位 Disposition-Notification-Options HTTP 标头
## <a name="details"></a>详细信息  
  
|                 |                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------|
|  产品名称   |                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                      |
| 产品版本 |                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                  |
|    事件 ID     |                                                              -                                                              |
|  事件源   |                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                    |
|    组件    |                                                         AS2 引擎                                                          |
|  符号名称  |                               AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError                                |
|  消息正文   | AS2 解码器无法定位生成 MDN 所必需的 Disposition-Notification-Options HTTP 标头。 |
  
## <a name="explanation"></a>解释  
 此错误/警告/信息事件表明接收管道无法生成 MDN，因为传入的 AS2 消息不包含 Disposition-Notification-Options 标头，该标头指出是否必须对 MDN 进行签名以及必须使用哪个 MIC 算法。  
  
## <a name="user-action"></a>用户操作  
 若要解决此错误，请让 AS2 消息的发送方在消息中包含 Disposition-Notification-Options 标头，然后重新发送消息。