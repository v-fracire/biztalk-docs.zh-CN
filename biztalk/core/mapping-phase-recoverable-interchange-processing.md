---
title: 映射阶段 （可恢复的交换处理） |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 544d85c7-bc47-46c1-8990-82b48a8f2f23
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20b3e45cf337702457dc8e5986db54df6bea5e5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262309"
---
# <a name="mapping-phase-recoverable-interchange-processing"></a>映射阶段 （可恢复的交换处理）
默认情况下，当交换一条消息在接收端口的映射阶段失败时，整个交换将挂起。 你可以通过添加名为的属性来更改此行为**BTS。SuspendMessageOnMapFailure**消息上下文中，并且，通过设置的上下文属性的值`True`从管道组件。 当此属性设置为`True`，终结点管理器将放置在挂起队列中的映射过程中失败，并继续处理剩余的消息交换中的消息。  
  
 下面的代码设置的值**SuspendMessageOnFailure**属性为 True。  
  
```  
  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
    bool bSuspend = true;  
    inmsg.Context.Write("SuspendMessageOnMappingFailure", "http://schemas.microsoft.com/BizTalk/2003/system-properties", bSuspend);   
    …  
}  
  
```