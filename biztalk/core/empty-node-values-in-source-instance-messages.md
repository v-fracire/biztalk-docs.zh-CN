---
title: 源中的空节点值实例消息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76f9d7c8-5a82-41e9-9077-7b1ddd80a837
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d847aace487d7b7ebd472ec96173e38315df529
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976614"
---
# <a name="empty-node-values-in-source-instance-messages"></a>源实例消息中的空节点值
在测试映射时，有时可能并不需要全部 schema 节点中的内容。  

## <a name="ceate-empty-node-values"></a>请空节点值  

1. 使用 BizTalk 编辑器生成实例数据。 有关生成实例数据的详细信息，请参阅[如何生成实例消息](../core/how-to-generate-instance-messages.md)。  

2. 在文本编辑器中打开输入实例消息，删除希望为空的元素和属性中的数据，然后保存修改后的实例文件。  

3. 在验证和测试架构之后，配置 BizTalk 映射器以使用刚刚修改过的文件。 在“属性”窗口中设置用于架构的文件。 有关设置属性的详细信息，请参阅**映射文件属性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

## <a name="see-also"></a>请参阅  
- [如何生成实例消息](../core/how-to-generate-instance-messages.md)   
- **架构属性参考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
