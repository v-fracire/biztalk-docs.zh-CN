---
title: 无法导入客户端终结点配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8375e153-ed1c-4bf4-b461-ac026a4b3478
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f3faa6a12bee397edcadb3f15c12a47d763fdce
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987182"
---
# <a name="unable-to-import-client-endpoint-configuration"></a>无法导入客户端终结点配置
## <a name="details"></a>详细信息  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  产品名称   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 产品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件 ID     |                                         0                                          |
|  事件源   |                                         0                                          |
|    组件    |                                         0                                          |
|  符号名称  |                                         0                                          |
|  消息正文   |                   无法导入客户端终结点配置                   |
  
## <a name="explanation"></a>解释  
 对于此错误可能有多种解释。 配置文件可能包含无效的字符。 根元素可能丢失。 根级别的数据可能无效。  
  
## <a name="user-action"></a>用户操作  
 验证配置文件是否有效。 尝试使用服务配置编辑器中打开配置文件 (**svcConfigEditor.exe**)，并验证每个属性。