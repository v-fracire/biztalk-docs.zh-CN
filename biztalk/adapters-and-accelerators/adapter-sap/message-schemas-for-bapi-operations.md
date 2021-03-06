---
title: BAPI 操作的消息架构 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAPI operations, message schemas for
- BAPI operations, message structure for
- BAPI operations, message actions for
ms.assetid: ef4d88e8-f31a-4b68-a303-6885b6f8c083
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 796e7beb428e6f9a4f0df63eff9cf45e9d5410bb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995214"
---
# <a name="message-schemas-for-bapi-operations"></a>BAPI 操作的消息架构
以下各节介绍的消息架构和消息操作用于在调用 Bapi[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]作为业务对象的方法。 此外可以在适配器上的 RFC 操作作为调用 Bapi。 有关用于调用 Rfc 的消息的详细信息，请参阅[RFC 操作的消息架构](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。 无论调用在适配器上的 BAPI 的方式，该适配器始终为 SAP 系统上的 RFC 调用 BAPI。 有关如何概述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支持 Bapi，请参阅[sap Bapi 的操作](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。  

## <a name="message-structure-for-business-object-operations"></a>对业务对象操作的消息结构  
 下表显示了用于调用 BAPI 作为业务对象方法的消息架构。  

|运算|XML 结构|Description|  
|---------------|-------------------|-----------------|  
|[BUSOBJ_METHOD]|`<[BUSOBJ_METHOD] xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]>`|调用上的 SAP 系统的业务对象方法。<br /><br /> 支持导入、 更改和表参数。|  
|[BUSOBJ_METHOD]响应|`<[BUSOBJ_METHOD]Response xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]Response>`|业务对象方法响应。<br /><br /> 导出，更改，并支持表参数。<br /><br /> **请注意**默认情况下，表参数不显示在响应消息。 如果您需要在响应消息中的表参数，您必须在请求消息中传递空表参数。|  

 [VERSION] = 消息版本字符串;例如， http://Microsoft.LobServices.Sap/2007/03。  

 [BUSOBJ_METHOD] = 业务对象方法; 的名称例如，CREATEFROMDAT2。  

 [IN_PARAM_NAME] = BAPI 导入参数的名称。  

 [OUT_PARAM_NAME] = BAPI 导出参数的名称。  

 [INOUT_PARAM_NAME] = BAPI 更改参数的名称。  

 [TABLE_PARAM_NAME] = BAPI 表参数的名称。  

 [STRUCT_PARAM_NAME] = BAPI 结构参数的名称。  

## <a name="message-actions-for-business-object-operations"></a>对业务对象操作的消息操作  
 下表显示了用于调用 Bapi 作为业务对象方法的消息操作。  


|        运算         |                            消息操作                             |                                                   示例                                                    |
|--------------------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|     [BUSOBJ_METHOD]      |     [VERSION] /Bapi/ [BUSOBJ_NAME] / [BUSOBJ_METHOD] / [BAPI_RFC_NAME]      |     http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2      |
| [BUSOBJ_METHOD]响应 | [VERSION] /Bapi/ [BUSOBJ_NAME] / [BUSOBJ_METHOD] / [BAPI_RFC_NAME] / 响应 | http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2/response |

 [VERSION] = 消息版本字符串;例如， http://Microsoft.LobServices.Sap/2007/03。  

 [BUSOBJ_NAME] = 业务对象中; 的名称例如，BUS2032。  

 [BUSOBJ_METHOD] = 的业务对象; 方法例如，CREATEFROMDAT2。  

 [BAPI_RFC_NAME] = BAPI; 的 RFC 名称例如，BAPI_SALESORDER_CREATEFROMDAT2。  

## <a name="see-also"></a>请参阅  
 [消息和消息架构用于 mySAP Business Suite 的 BizTalk 适配器](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)