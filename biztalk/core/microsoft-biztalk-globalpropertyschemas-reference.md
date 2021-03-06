---
title: Microsoft.BizTalk.GlobalPropertySchemas 引用 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2acf3083-a0a9-483f-88bf-8023d9933e1e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8e24cee64b5f03b212fabd7003f8ba3586b1c22
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982878"
---
# <a name="microsoftbiztalkglobalpropertyschemas-reference"></a>Microsoft.BizTalk.GlobalPropertySchemas 引用
**Microsoft.BizTalk.GlobalPropertySchemas**命名空间包含使用各种 BizTalk Server 组件的属性的属性架构。 此命名空间包含 BizTalk 引擎使用的系统属性、每个传输用于处理配置的特定于传输的属性，以及用于配置管道组件的属性。  

## <a name="namespace-schemas"></a>Namespace 架构  

 下表显示了中包含的全局属性架构**Microsoft.BizTalk.GlobalPropertySchemas**命名空间。  


|                                                                                                                                                              属性架构                                                                                                                                                              |                                                                                                                                                               功能区和说明                                                                                                                                                                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                          bts-btf2-properties.xsd                                                                                                                                                          |                                                                                                                                                                     属性架构。                                                                                                                                                                      |
|                                             btf2-endpoints-header.xsd<br /><br /> btf2-envelope.xsd<br /><br /> btf2-manifest-header.xsd<br /><br /> btf2-process-header.xsd<br /><br /> btf2-properties-header.xsd<br /><br /> btf2-receipt-header.xsd<br /><br /> btf2-services-header.xsd                                              |                                                                                                   定义 BizTalk 框架构造的架构。 这些架构专门用于 BizTalk 框架组装器和拆装器管道组件。                                                                                                   |
|                                                                                                                                                         bts-system-properties.xsd                                                                                                                                                         | 这是系统属性架构。 BizTalk 引擎使用此架构中的大多数属性。 某些属性可用于消息路由。 有关可用于消息路由的属性的详细信息，请参阅**消息上下文属性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 |
|                                                                                                                                                        bts-endpoint-properties.xsd                                                                                                                                                        |                                                                                                                                                           这是内部属性架构。                                                                                                                                                            |
|                                                                                                                                      bts-mime-properties.xsd<br /><br /> bts-xmlnorm-properties.xsd                                                                                                                                       |                                                                                                      这些属性架构用于以下管道组件：MIME、XML、平面文件、BizTalk 框架组装器和拆装器等管道组件。                                                                                                      |
|                                                                                                                                                    bts-messagetracking-properties.xsd                                                                                                                                                     |                                                                                                                                                           跟踪引擎使用此架构。                                                                                                                                                           |
| bts-file-properties.xsd<br /><br /> bts-ftp-properties.xsd<br /><br /> bts-http-properties.xsd<br /><br /> bts-pop3-properties.xsd<br /><br /> bts-smtp-properties.xsd<br /><br /> soap-encoding_1__1.xsd<br /><br /> soap-envelope_1__1.xsd<br /><br /> bts-soap-properties.xsd<br /><br /> bts-WindowsSharePointServices-properties.xsd |                                                               这些是特定于传输的属性架构。 不同的传输使用这些架构来传送特定的传输信息和配置。 传输的详细信息，请参阅[使用适配器](../core/using-adapters.md)。                                                                |
|                                                                                                                                                        XLANGsBizTalkProperties.xsd                                                                                                                                                        |                                                                                                                                                        业务流程引擎使用此架构。                                                                                                                                                         |

## <a name="see-also"></a>请参阅  
 [关于 BizTalk 项目中包含的 BizTalk 命名空间引用](../core/about-biztalk-namespace-references-included-in-biztalk-projects.md)