---
title: 数据元素太短 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a22c0551-3262-476c-a6c6-2fd214331244
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db14770404a45ddbfd3aea6ed71e9b8b22417515
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005294"
---
# <a name="data-element-too-short"></a>数据元素太短
## <a name="details"></a>详细信息  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  产品名称   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 产品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件 ID     |                                           -                                            |
|  事件源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    组件    |                                       EDI 引擎                                       |
|  符号名称  |                                           -                                            |
|  消息正文   |                                 数据元素太短                                 |
  
## <a name="explanation"></a>解释  
 此错误/警告/信息事件表明 EDI 接收管道或 EDI 发送管道无法处理传入的交换，因为数据元素短于架构指定的最小长度。  
  
## <a name="user-action"></a>用户操作  
 若要解决此错误，延长函数太短，因此其值大于最小长度的交换中的数据元素。 若要确定最小长度，打开 \XSD_Schema 文件夹中的架构、 数据元素 id，搜索和识别 minLength 值是什么。