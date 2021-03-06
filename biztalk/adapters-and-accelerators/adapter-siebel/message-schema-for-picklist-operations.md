---
title: 选择列表操作的消息架构 |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- picklist operations, message schemas for
- picklist operations, message actions
- picklist operations, message
ms.assetid: c0b62a8c-5a68-47ea-8676-1580601b5ec9
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d72a16e99e38649a6fb8d74178d2b5da1d059dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221901"
---
# <a name="message-schema-for-picklist-operations"></a>选择列表操作的消息架构
选择列表是在业务组件中的特殊字段类型。 它们表示的用户可能会从其选取分配的单个值的值的集合。 选择列表都是不同的类型。 有关选择列表和它们的类型的详细信息，请参阅 Siebel 文档。  
  
 选择列表类型之一，绑定的静态选择列表，作为枚举的选择列表进行展示的适配器在设计时生成的适配器的元数据中的类型。 这包含一组静态在运行时必须选择列表类型为指定的值。  同时为静态绑定选择列表中指定一个值，必须始终指定一个属于集的值。  
  
 下面的示例显示一个静态绑定的选择列表类型的架构：  
  
```  
<element name="[FIELD_NAME]RequiredPickListType" nillable="true" type="ns1:[FIELD_NAME]RequiredPickListType" />  
<simpleType name="[FIELD_NAME]RequiredPickListType">  
<restriction base="string">  
  <enumeration value="value1" />  
  <enumeration value="value2" />  
  …  
</restriction>  
</simpleType>  
```  
  
 [字段名] = 业务组件中的选择列表字段名称  
  
 下面的内容表示一个绑定的静态选择列表类型的代理体验：  
  
```  
[BC]InsertRecord[] insertRecs = new [BC]InsertRecord[1];  
insertRecs[0] = new [BC]InsertRecord();  
insertRecs[0].[BC_STATIC_PICKLIST_FIELD] = [BC_PICKLIST_FIELD_NAME]OptionalPickListType.value1;  
```  
  
 [BC_STATIC_PICKLIST_FIELD] = BC 静态绑定的选择列表字段  
  
## <a name="see-also"></a>另请参阅  
 [消息和用于 Siebel eBusiness Applications 的 BizTalk Adapter 的消息架构](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)