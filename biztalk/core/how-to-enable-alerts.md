---
title: 如何启用警报 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Enable-Alerts command [BAM]
- managing [BAM definitions], enabling alerts
- alerts, enabling
ms.assetid: 18f494b7-54fb-4aaf-89d1-7e3fe91f35c6
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9fee863613feea040e05856d8246f94b4a3f835
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969150"
---
# <a name="how-to-enable-alerts"></a>如何启用警报
管理员使用**启用警报**命令以启用所有指定的视图上的警报。  
  
### <a name="to-enable-an-alert"></a>若要启用的警报  
  
1. 按如下所示打开命令提示符： 单击**启动**，单击**运行**，类型**cmd**，然后单击**确定**。  
  
2. 通过在命令提示符处键入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，导航到跟踪文件夹。 按 **Enter**。  
  
3. 类型**bm 启用警报的视图：\<视图名称\>**。  
  
   > [!NOTE]
   >  如果您已经将 BAM 配置作为 XML 导出，则不要修改与警报相关的 XML。 如果您更改与警报相关的 XML 并部署这些更改，则 bm.exe 将检测到该更改并启用 BAM 警报。  
  
4. 按 **Enter**。  
  
## <a name="see-also"></a>请参阅  
 [管理 BAM 动态基础结构](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理实用程序](../core/bam-management-utility.md)   
 [在此处输入链接说明](../core/how-to-disable-alerts.md)