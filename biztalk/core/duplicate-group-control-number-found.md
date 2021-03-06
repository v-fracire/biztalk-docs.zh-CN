---
title: 找到的组控制编号重复 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1badc033-42fd-4992-ad36-b53047ba7817
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66fd37bbfc5be81f7a7301f6313745a29ec180de
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001430"
---
# <a name="duplicate-group-control-number-found"></a>找到重复的组控制编号
## <a name="details"></a>详细信息  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  产品名称   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 产品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件 ID     |                                           -                                            |
|  事件源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    组件    |                                       EDI 引擎                                       |
|  符号名称  |                                           -                                            |
|  消息正文   |                          找到重复的组控制编号                          |

## <a name="explanation"></a>解释  
 此错误/警告/信息事件表明 EDI 接收管道可以不处理传入的交换由于具有相同的交换、 组或事务集控制编号与以前接收的交换。 这将导致失败，只要启用了相应的重复控制编号检查。  

## <a name="user-action"></a>用户操作  
 若要解决此错误，请执行以下操作之一：  

- 确保发送给 BizTalk Server 的交换具有与之前交换不同的组控制编号（如果启用相应的重复控制编号检查）。  

- 禁用重复组控制编号检查。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理控制台中，右键单击相应的一方，然后为作为交换发送方的参与方打开“EDIFACT 交换处理属性”或“X12 交换处理属性”对话框。 若要禁用 EDIFACT 交换检查，请清除“检查交换中重复的 UNG5 (组控制编号)”属性。 若要禁用 X12 交换检查，请清除“检查交换中重复的 GS6 (组控制编号)”属性。
