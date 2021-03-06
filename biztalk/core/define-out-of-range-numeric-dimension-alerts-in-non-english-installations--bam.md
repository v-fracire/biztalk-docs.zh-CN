---
title: 如何在非英语安装中定义的范围外数值维度警报 |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f1e0373-eadf-4c6d-9a38-a34d847f310f
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea63008680c026eded843e32a7b2c6ff26dc0bf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238685"
---
# <a name="how-to-define-out-of-range-numeric-dimension-alerts-in-non-english-installations"></a>如何在非英语系统中定义“超出范围”数值维度警报
当设置包括一个值，在非英语安装上定义的数值范围维度之外的条件的警报，你必须手动修改 BAM 定义一同保存本地化版本的字符串**超出范围**.  
  
 下表列出了一些本地化后的“超出范围”的值的示例。  
  
|语言代码|本地化字符串|  
|-------------------|----------------------|  
|CN|超出范围|  
|DE|Außerhalb des gültigen Bereichs|  
|ES|Fuera de rango|  
|FR|hors limites|  
|IT|Fuori intervallo|  
|JA|範囲外|  
|KO|범위를 벗어남|  
|TW|超過範圍|  
  
### <a name="to-define-out-of-range-alerts-in-non-english-installations"></a>在非英语系统中定义“超出范围”警报  
  
1.  导航到包含 BAM 定义 xml 文件的文件夹。  
  
2.  使用文本编辑器或 XML 编辑器，打开 BAM 定义文件。  
  
3.  查找数值维度的切片维度。 例如，如果名为切片器维度**Alerts_NumDim**，你将找到以下节点：  
  
    ```  
    <SlicerDimension Name="Alerts_NumDim">  
    <Level Name="(Out of Range)" />  
    </SlicerDimension>  
    ```  
  
4.  更改**范围**字符串值设为相应的本地化字符串。  
  
5.  保存文件，并部署该定义。  
  
## <a name="see-also"></a>另请参阅  
 [什么是 BAM 定义架构？](../core/what-is-a-bam-definition-schema.md)   
 [如何部署 BAM 定义](../core/how-to-deploy-bam-definitions.md)