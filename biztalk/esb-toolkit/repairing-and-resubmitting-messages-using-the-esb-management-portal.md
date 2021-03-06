---
title: 修复和重新提交消息使用 ESB 管理门户 |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43091cbd-77d1-4cbd-9190-2d423ce7d4df
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61602fb41a2c6754fe6d77d249e2ec8c2f40cd39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295253"
---
# <a name="repairing-and-resubmitting-messages-using-the-esb-management-portal"></a>修复和重新提交消息使用 ESB 管理门户
在本例使用一个预配置发送端口使用 ESB 错误处理器发送管道接收生成的业务流程或由 Microsoft BizTalk 中的失败的邮件路由机制生成的错误消息中的异常处理程序 ESB 错误消息服务器。 ESB 错误处理器规范化，使其更加丰富，并将它路由到 ESB 管理门户数据库。 门户监视传入的错误消息的数据库，并且可以生成通知的处理失败的订阅的用户的警报。 用户可以在门户错误查看器中打开的错误消息，编辑消息内容，然后重新提交以进行处理，该消息，如图 1 中所示。  
  
 ![修复消息](../esb-toolkit/media/ch3-repairingmessages.gif "Ch3 RepairingMessages")  
  
 **图 1**  
  
 **修复和重新提交消息使用 ESB 管理门户**  
  
 作为使用示例包括 ESB 管理门户[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]演示此用例。 它提供完整图形环境进行编辑，然后重新提交消息;它还支持警报、 通知和消息重新提交审核。  
  
 有关详细信息，请参阅[处理异常和错误消息](../esb-toolkit/working-with-exceptions-and-fault-messages.md)。