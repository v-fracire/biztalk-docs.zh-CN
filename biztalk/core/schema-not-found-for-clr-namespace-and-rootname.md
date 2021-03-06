---
title: 找不到 CLR Namespace 和 rootName 的架构 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db283d81-1cb0-460d-ace4-49a91ceb4a02
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a830d46a439ad85e5e9e3d54afaca688dac201ca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966342"
---
# <a name="schema-not-found-for-clr-namespace-and-rootname"></a>找不到 CLR 命名空间和 rootName 的架构
## <a name="details"></a>详细信息  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  产品名称   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 产品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件 ID     |                                           -                                            |
|  事件源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    组件    |                                       EDI 引擎                                       |
|  符号名称  |                               SchemaNotFoundForCLRAndRN                                |
|  消息正文   |              找不到 CLR Namespace 架构 ={0}和 rootName = {1}               |
  
## <a name="explanation"></a>解释  
 此错误/警告/信息事件表明接收管道使用与交换关联的根名称以及与为交换解析的参与方关联的命名空间无法找到文档架构。  
  
## <a name="user-action"></a>用户操作  
 若要解决此错误，请确保从交换中获取的根名称以及从解析后的参与方的属性中确定的命名空间都与部署的架构相对应。 BizTalk 从交换中的文档类型和版本中确定根名称。 BizTalk 确定在将架构从默认目标 Namespace 字段 （对于默认架构） 或"启用自定义事务集定义"网格 （适用于自定义架构） 中交换处理属性。