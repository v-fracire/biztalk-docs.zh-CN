---
title: 开发探测管道组件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], probing
- IProbeMessage interface
- pipeline interfaces, IProbeMessage
ms.assetid: c3da467d-5270-4c7f-9c38-ce9989bf1b63
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0be44929609eaba5ec30a6e40c1bdda14192e351
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987350"
---
# <a name="developing-a-probing-pipeline-component"></a>开发探测管道组件
任何管道组件 （一般、 组装或拆装） 都可以实现`IProbeMessage`接口是否必须支持消息探测功能。 探测组件用于具有的管道阶段**第一个匹配**执行模式。 在此类阶段中，BizTalk 消息引擎将消息的开始部分提供给组件，以便确定组件是否识别该消息的格式。 如果组件识别格式，则会将整个消息交给此组件进行处理。  
  
 **IProbeMessage**接口公开单个方法**探测**，这使组件可以检查消息的开始部分。 返回值确定此组件是否已运行。 以下步骤说明了 BizTalk 消息引擎如何运行需要识别的阶段：  
  
1. 如果阶段不包含任何组件，则该阶段不运行，消息交给随后的阶段进行处理。  
  
2. 检查组件是否实现**IProbeMessage**接口。 如果没有，消息引擎将调用该组件。 阶段处理完成，消息交给下一个阶段。  
  
3. **探测**调用方法。 如果返回值是 **，则返回 True**，该组件已运行。 然后，阶段处理完成，消息交给下一个阶段。  
  
4. 消息引擎获取阶段中的下一个组件。 如果没有其他组件并且所有组件都尚未运行，则生成一个错误，提示您管道处理失败。 如果没有其他组件并且至少有一个已运行，则处理完成。  
  
   如果阶段不需要识别 (例如，执行模式是**所有**)，消息引擎调用组件，而无需为第一个查询**IProbeMessage**接口并调用**探测**方法。  
  
## <a name="see-also"></a>请参阅  
 [开发常规管道组件](../core/developing-a-general-pipeline-component.md)   
 [开发汇编程序管道组件](../core/developing-an-assembling-pipeline-component.md)   
 [开发拆装管道组件](../core/developing-a-disassembling-pipeline-component.md)   
 [报告来自管道组件的错误](../core/reporting-errors-from-pipeline-components.md)   
 [配置本地管道组件](../core/configuring-native-pipeline-components.md)   
 [部署管道组件](../core/deploying-pipeline-components.md)