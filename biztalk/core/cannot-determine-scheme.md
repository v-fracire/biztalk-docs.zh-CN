---
title: 无法确定方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cc6e50b-33f5-4a88-b35d-075fdf8d79b2
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6086562f593b7ca04db63b7fb41f5cf128afe9d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007166"
---
# <a name="cannot-determine-scheme"></a>无法确定方案
## <a name="details"></a>详细信息  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  产品名称   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 产品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件 ID     |                                         0                                          |
|  事件源   |                                         0                                          |
|    组件    |                                         0                                          |
|  符号名称  |                                         0                                          |
|  消息正文   |                 无法确定方案；请指定有效的绑定。                  |
  
## <a name="explanation"></a>解释  
 已经指定的传输绑定元素没有方案。  
  
## <a name="user-action"></a>用户操作  
 选择一个有效的绑定，并确保传输绑定元素具有有效的方案。 如果使用自定义绑定，请确保指定了有效的传输绑定元素。  
  
 有关其他信息，请参阅中的以下资源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]帮助：  
  
-   [配置 WCF-Custom 适配器](../core/configuring-the-wcf-custom-adapter.md)