---
title: PIP 实现 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PIPs
- PIPs, element-level constraints
- Document Type Definitions (DTDs)
- PIPs, schemas
- examples, schemas
- schemas, examples
- PIPs, about PIPs
- element-level constraints
- PIPs, DTDs
- schemas, PIPs
- XML Schema Definition files (XSDs)
- Partner Interface Processes (PIPs)
- DTDs, XSDs
- schemas, XSDs
ms.assetid: 0d964223-e0b6-4377-b26a-5fdc89ec81f4
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba85938e2e0da2b8ee09de476c81acdf202b449c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982998"
---
# <a name="pip-implementation"></a>PIP 实现
RosettaNet 合作伙伴接口流程 (Pip) 定义在供应链中的贸易合作伙伴之间的业务流程。 Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]提供了一组 Pip 的开箱，你可以创建其他 Pip。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 支持 RosettaNet 组织定义的所有 Pip。  
  
 有关详细信息，请参阅[RosettaNet Pip](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)。  
  
## <a name="schemas-in-btarn"></a>BTARN 中的架构  
 RosettaNet 将所有 PIP 消息架构都指定为文档类型定义 (DTD) 形式。 参与业务文档交换的贸易伙伴必须遵守这些 DTD。 但是，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]实施这些 Dtd 作为 XML 架构定义文件 (Xsd)，因为 Microsoft BizTalk Server 使用 xsd 而不是 Dtd 来表示文档。 XSD 在功能方面可以取代 DTD，并可以表示本地消息指南中提供的大多数信息。  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 还支持 RosettaNet 组织最新发布的、使用 XSD 规范的下一代 PIP。  
  
 要实施新的 PIP，必须将 PIP 的 DTD 形式转换为 XSD。 下载与从 RosettaNet 网站下载，网址 PIP 相关联的 DTD [ http://go.microsoft.com/fwlink/?linkid=33859 ](http://go.microsoft.com/fwlink/?linkid=33859)。 然后你可以基于 PIP 创建 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 流程配置的配置文件。 有关详细信息，请参阅[并入新的合作伙伴接口流程](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)。  
  
 可以基于现有的配置文件新建一个流程配置的配置文件。 有关详细信息，请参阅[如何创建或编辑流程配置](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。 可以基于相同合作伙伴之间的同一个流程配置的配置文件创建多个协议。 但是，一次只能激活一个协议。 若要创建并激活协议，请参阅[创建或编辑协议](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 利用对以下 RosettaNet 头的 RosettaNet 消息指南约束来实施 XSD：  
  
-   RNIF 1.1 和 RNIF 2.01 的前导头  
  
-   RNIF 1.1 和 RNIF 2.0 的服务头  
  
-   RNIF 2.0 的传递头  
  
-   RNIF 1.1 和 RNIF 2.01 的所有信号消息的服务内容。  
  
## <a name="sample-schemas"></a>示例架构  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 安装程序将安装 Pip 中一组\<*驱动器*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\schemas 中找到。 这些 PIP 仅用作示例。 强烈建议你在将其用于生产过程之前，将这些架构与最新发布的 RosettaNet PIP 规范和消息指南进行比较。 BTARN 支持所有 RosettaNet PIP 的实施。  
  
## <a name="element-level-constraints-in-btarn"></a>BTARN 中的元素级约束  
 在 BTARN 中，将 PIP 消息指南文档中指定的元素级约束作为流程配置设置来实施。 运行时组件使用流程配置来确定处理特定 PIP 的方式。  
  
 要实施新的 PIP，必须通过新建流程配置的配置文件来应用对 PIP 的消息指南约束。 这一操作在 BTARN 管理控制台中实现。 有关详细信息，请参阅[如何创建或编辑流程配置](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。  
  
 流程配置配置文件映射到 RosettaNet PIP 规范中所示[使用 PIP 规范创建流程配置](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)。  
  
## <a name="see-also"></a>请参阅  
 [BizTalk Accelerator for RosettaNet 向 BizTalk Server 的添加](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [贸易合作伙伴协议](../../adapters-and-accelerators/accelerator-rosettanet/trading-partner-agreements.md)   
 [RosettaNet PIP](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)
