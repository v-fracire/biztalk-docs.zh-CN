---
title: 使用管道设计器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Pipeline Designer, how to
- pipelines, Pipeline Designer
ms.assetid: bdb2f5c7-f8a2-4bd6-a8d8-8b7a64f97bd0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f5a3e2d9d3dad37372fc01f6446f0c06272589a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019019"
---
# <a name="using-pipeline-designer"></a>使用管道设计器
管道设计器是一个以 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 为宿主的图形编辑器，使用该设计器，可以创建新的管道；查看 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 附带的管道模板；在管道中移动管道组件以及配置管道、阶段和管道组件。  
  
 管道设计器采用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 外壳程序的三个主要工具来丰富您的设计体验：  
  
- “属性”窗口，用于查看和修改管道对象的大多数特性。  
  
- 工具箱，用作设计图面的来源。  
  
- 设计图面，用于从工具箱拖放组件。  
  
  下图显示了管道设计器环境。  
  
  ![管道设计器编辑环境](../core/media/ebiz-prog-usepipe.gif "ebiz_prog_usepipe")  
  管道设计器环境示意图  
  
  管道设计器与 BizTalk 项目模板进行了集成，以增强您的开发体验。 在使用项目系统创建一个新的 BizTalk 项目之后, 可以使用**添加新项**命令**文件**菜单添加到你的解决方案的管道。 有关 BizTalk 项目模板的详细信息，请参阅[使用 BizTalk 项目系统](../core/using-the-biztalk-project-system.md)。  
  
> [!NOTE]
>  在早期版本的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，管道的概念包含在消息通道和端口中，它定义了一组按固定顺序应用于文档的特定组件。 在此版本中，管道非常灵活，不仅可以随意重排管道的各个阶段的组件，还可以在管道内轻松插入多个自定义组件。  
  
 通过管道设计器设计图面，您可以绘制管道的图形表示形式。 在设计图面占据的主要部分[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]窗口并使您能够编辑属于 BizTalk 项目的管道。 通过单击设计图面上方的选项卡，可以在管道之间进行导航。  
  
 每个管道都由多个阶段构成，每个阶段包含一个或多个组件。 如果阶段中没有组件，则将显示带文本的水印，指示可以从工具箱插入形状。 向阶段中插入第一个形状之后，原来的文本将消失。 设计图面沿垂直方向显示管道，运行顺序为从上（开始）到下（结束）。  
  
 一样与其他常用的 Microsoft Windows 程序，您可以执行多项任务，如**开放**并**保存**从**文件**菜单。  
  
## <a name="see-also"></a>请参阅  
 [使用管道设计器创建管道](../core/creating-pipelines-with-pipeline-designer.md)   
 [使用管道设计器创建管道](../core/creating-pipelines-using-pipeline-designer.md)