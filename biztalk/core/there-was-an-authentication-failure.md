---
title: 出现身份验证错误 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36524da9-da91-41e7-bf73-7781cde20c80
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5548d448d2c0d45addc72639ad229cf4ee1bf37f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022347"
---
# <a name="there-was-an-authentication-failure"></a>出现验证错误
## <a name="details"></a>详细信息  
  
|                 |                                                                                                                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  产品名称   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                         |
| 产品版本 |                                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                     |
|    事件 ID     |                                                                                                 -                                                                                                 |
|  事件源   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                       |
|    组件    |                                                                                            EDI 引擎                                                                                             |
|  符号名称  |                                                                                         DescPartyNotFound                                                                                         |
|  消息正文   | 出现验证错误。 确保正在处理的消息存在匹配的参与方。 并且消息中的安全/密码信息与“参与方”配置匹配 |
  
## <a name="explanation"></a>解释  
 此错误/警告/信息事件表明接收管道无法处理传入的交换，因为 BizTalk Server 无法验证消息的发送方。  
  
## <a name="user-action"></a>用户操作  
 若要解决此错误，请执行以下操作之一：  
  
-   验证交换标头中的发送方限定符和标识符（对于 X12，为字段 ISA5 和 ISA6，对于 EDIFACT，为字段 UNB2.1 和 UNB2.2）是否与某个参与方的属性中的发送方限定符和标识符匹配（如“EDI 属性”对话框的“交换处理属性”页中所定义）。  
  
-   验证交换标头中的安全/密码信息（对于 X12，为字段 ISA3 和 ISA4，对于 EDIFACT，为字段 UNB6.1 和 UNB6.2）是否与某个参与方的属性中的安全/密码信息匹配（如“EDI 属性”对话框的“交换处理属性”页中所定义）。