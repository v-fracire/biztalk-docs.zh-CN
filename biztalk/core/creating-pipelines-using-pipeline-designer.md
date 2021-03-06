---
title: 使用管道设计器创建管道 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, processing messages
- pipelines, Pipeline Designer
- Pipeline Designer, about Pipeline Designer
ms.assetid: 858302d8-a912-4199-95e5-4322db789b4e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62e182440522e82f7ae6eaeaf52234161bee7483
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998606"
---
# <a name="creating-pipelines-using-pipeline-designer"></a>使用管道设计器创建管道
Microsoft BizTalk Server 主要处理 XML 文档格式。 通常，消息必须从本身格式转换为其 XML 表示形式，才能充分利用 BizTalk Server 的处理功能。 BizTalk Server 管道可对传入消息和传出消息执行这种转换，并执行其他特定于数据的操作（例如数据加密或解密、属性升级等）。 本部分提供有关管道和管道设计器的概念信息和任务特定信息。  
  
 管道的作用是在适配器接收消息后对消息进行准备以便服务器处理，或在服务器处理消息后对消息进行准备以便发送。  
  
 管道通常执行以下操作：  
  
- 从不同格式到 XML 格式的数据规范化。  
  
- 从 XML 格式到不同格式的数据转换。  
  
- 属性升级和降级。  
  
- 文档拆装和组装。  
  
- 文档解码和编码。  
  
- 文档解密和加密。  
  
- 文档签名和数字签名验证。  
  
  下图显示了在使用管道处理消息过程中涉及的工作流：  
  
  ![用于处理消息的工作流的图表。](../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")  
  消息处理工作流示意图  
  
  如图所示，消息将从适配器传递到接收管道，在管道中消息将转换为 XML。 然后，消息可由业务流程使用，或传递给发送管道，然后传递给发送适配器。  
  
  有关使用键盘快捷键的管道设计器的信息，请参阅[管道设计器键盘快捷方式](../core/pipeline-designer-keyboard-shortcuts.md)。  
  
## <a name="in-this-section"></a>本节内容  
  
-   [关于管道、阶段和组件](../core/about-pipelines-stages-and-components.md)  
  
-   [使用管道设计器](../core/using-pipeline-designer.md)  
  
-   [使用管道设计器创建管道](../core/creating-pipelines-with-pipeline-designer.md)  
  
-   [配置本地管道组件](../core/configuring-native-pipeline-components.md)  
  
-   [如何部署管道](../core/how-to-deploy-pipelines.md)  
  
-   [如何确保管道安全](../core/how-to-secure-pipelines.md)