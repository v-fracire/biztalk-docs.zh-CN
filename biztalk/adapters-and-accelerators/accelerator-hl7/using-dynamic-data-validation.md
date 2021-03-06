---
title: 使用动态数据验证 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic data validation
- validating, dynamic data
ms.assetid: 8dac7f74-92a7-447c-97bf-b1f3ce39b614
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b0ff37ff260ca11e594a208c125f229e2961c01
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967158"
---
# <a name="using-dynamic-data-validation"></a>使用动态数据验证
动态数据验证的一个重要部分就验证针对动态数据，其中包括验证的消息格式和消息内容的消息内容。 文档架构，MicrosoftBizTalk 服务器实现在 XSD 文件中，定义和验证消息格式。 业务规则定义消息内容，其中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]通过业务规则引擎策略验证。 内容验证可以包括确认消息实例中的数据的相对频率可能会更改数据匹配。 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]以动态方式实现这种类型的验证，以便可以更新在生产环境中，此数据而无需重新编译代码或关闭服务。  
  
## <a name="validate-and-expose-data"></a>验证并公开的数据  
 在执行动态数据验证 (DDV) 有两个步骤：  
  
- 公开的数据。  
  
- 将使用该数据的验证规则的应用。  
  
  DDV 提供了用于存储、 公开，和动态数据缓存的以下支持：  
  
- 业务规则引擎或消息类执行验证。  
  
- 业务规则引擎数据库表列词汇通过将数据公开。 业务规则引擎通过实现从管道或业务流程中运行的规则集来验证针对消息此动态数据。  
  
- 现有的 SQL 接口，如 SQL 企业管理器和查询分析器中，在设计时是被动的公开动态数据。  
  
- 业务规则引擎数据库表列词汇定义显示在运行时动态数据。  
  
- 业务规则引擎在运行时公开的消息实例数据。  
  
- 业务规则引擎 XML 文档词汇定义在设计时显示的消息实例数据。  
  
- 您可以编写规则在设计时在业务规则编辑器用户界面中或直接在业务规则语言 (BRL) XML 文本编辑器中。  
  
  有关业务规则和业务规则引擎的详细信息，请参阅"开发与业务规则"BizTalk Server 帮助中。  
  
## <a name="extending-ddv"></a>扩展 DDV  
 如果更改基于 HL7 的跨字段验证规则或数据类型验证时，您必须注意两件事：  
  
-   如果修改现有规则，您不需要重新部署。  
  
-   如果你创建或删除影响的管道组件的新规则，然后你必须重新编译。  
  
## <a name="see-also"></a>请参阅  
 [编程指南](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [消息充实教程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)