---
title: 实例消息处理使用可分辨字段 |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b8f3f77-5385-4294-b441-bcb28bdc51b4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4dca22ff1b09a0d1cfb261a9d5726da8b1b17b1
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
ms.locfileid: "22257509"
---
# <a name="instance-message-processing-using-distinguished-fields"></a>使用可分辨字段处理实例消息
将属性提升通过 **可分辨字段** 机制不需要的属性架构创建。 因为所有属性提升，与你使用 **升级属性** 对话框中，这是可访问通过使用 **升级属性** 属性 **架构** 节点在消息架构中，或通过使用 **Promote & #124;显示升级** 命令 **BizTalk** 或快捷菜单。  
  
 在 **升级属性** 对话框框中，确保 **可分辨字段** 在对话框中的右侧选择选项卡。 然后展开以查找并选择对话框左侧的架构树中节点 **Field 元素** 节点或 **字段特性** 你想要将提升为可分辨的字段，然后单击的节点 **添加**。 有关将提升到的属性的分步说明**可分辨字段**使用**升级属性**对话框中，请参阅[将数据复制到作为 Distinguished 消息上下文字段](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)。  
  
> [!NOTE]
>  你还可以升级 **记录** 到属性架构，但是只有当中的字段元素节点的节点 **内容类型** 属性 **记录** 节点设置为 **SimpleContent**。  
  
 若要删除的可分辨字段会提升的属性集从一个节点，选择提升的属性上 **可分辨字段** 卡，然后单击 **删除**。  
  
 在使用可分辨字段机制升级属性时，XML 架构定义 (XSD) 语言片断将添加到根元素的批注子元素中。 以下示例的片断中显示了使用可分辨字段机制升级的两个属性：  
  
```  
<b:properties>  
    <b:property distinguished="true"  
        xpath="/*[local-name()='Record' and namespace-  
         uri()='http://BizTalk_Server_Project1.Schema11']/*[local-  
         name()='test']/*[local-name()='Field1']" />  
    <b:property distinguished="true"  
        xpath="/*[local-name()='Record' and namespace-  
         uri()='http://BizTalk_Server_Project1.Schema11']/*[local-  
         name()='test']/*[local-name()='Field5' and position()='1']" />  
</b:properties>  
```  
  
## <a name="see-also"></a>另请参阅  
 [使用与控件消息处理的消息内容的方法](../core/ways-to-use-message-content-to-control-message-processing.md)   
 [如何将数据复制到可分辨的字段的消息上下文](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)