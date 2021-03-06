---
title: 管理 BizTalk Server 性能设置 |Microsoft Docs
description: 使用设置仪表板来更新 BizTalk 组、 主机和 BizTalk Server 中设置的主机实例
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ca56a981-a255-4c4d-82f8-a57d390e425e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19acfa50ecbcaf46cb796630e88d292283f4631e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999766"
---
# <a name="manage-biztalk-server-performance-settings"></a>管理 BizTalk Server 性能设置
  
 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] BizTalk Server 中整理性能设置，并提供了一个中央控制台来管理这些设置。 这可以帮助：  
  
-   提高可设置的属性的可发现的性
  
-   因为所有设置在单个位置现在均可访问，可以导出/导入轻松减少时解决方案
  
-   提供的性能优化级别的整体视图上给定的 BizTalk 部署完成
  
## <a name="why-use-it"></a>为什么要使用它？  
 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 面向需要广泛地调整性能优化的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 设置的 IT 管理员。  
  
 您可以使用 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 修改 BizTalk 组以及该组中 BizTalk 主机和 BizTalk 主机实例的设置。  
  
 若要了解有关组、 主机和主机实例设置的详细信息，请参阅[如何修改组设置](../core/how-to-modify-group-settings.md)，[如何修改主机设置](../core/how-to-modify-host-settings.md)，和[如何修改主机实例设置](../core/how-to-modify-host-instance-settings.md).  
  
## <a name="prerequisites"></a>必要條件 
 您可以从 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 管理控制台启动 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 有关如何管理的信息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]性能设置，请使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理控制台中，请参阅[使用 BizTalk Server 管理控制台](../core/using-the-biztalk-server-administration-console.md)。  
  
## <a name="where-do-i-start"></a>如何开始？  
 可以用以下任意一种方式访问 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]：  
  
- 启动[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理控制台中，右键单击**BizTalk 组**在控制台树中，然后选择**设置**。  
  
- 右键单击下的任一主机**平台设置**节点中 MMC，然后单击**设置**。 这将启动 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]，您可以修改与该主机相关的设置。  
  
- 右键单击下的任何主机实例**平台设置**节点中 MMC，然后单击**设置**。 这将启动 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]，您可以修改与该主机实例相关的设置。  
  
## <a name="export-and-import-settings"></a>导出和导入设置  
 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 可用于从 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 环境导出设置，并将其导入另一 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 环境，从而缩短解决方案的推出时间。 当管理员尝试在测试环境中调整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 性能时，它们特别有用，而且它们可将设置导入到生产环境中，从而获得期望的结果。  
  
 有关如何使用导入/导出[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]用户界面，请参阅[导入或导出 BizTalk 设置使用设置仪表板](how-to-import-biztalk-settings-using-settings-dashboard.md)。
  
## <a name="scripting-support"></a>脚本支持
 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 不仅提供了一个用于管理 BizTalk 设置的中央用户界面，而且还可确保所有设置和导入/导出任务都可以通过 API 和命令行选项来访问。 这使得 BizTalk Server 管理员能够自动执行与 BizTalk Server 设置相关的任务。 作为脚本的支持的一部分：  
  
- 可以访问和修改通过 WMI 类所有组设置： `MSBTS_GroupSetting`  
  
- 可以访问和修改通过 WMI 类所有主机设置： `MSBTS_HostSetting`  
  
- 可以访问和修改通过 WMI 类所有主机实例设置： `MSBTS_HostInstanceSetting`  
  
- 导入和导出操作可以通过访问**BTSTask.exe**命令：`ExportSettings`和 `ImportSettings`  
  
  有关如何使用 BTSTask.exe 命令行实用程序导入/导出的详细信息，请参阅[导入或导出 BizTalk 设置使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。  
  
## <a name="next"></a>Next  
  
-   [使用设置仪表板进行 BizTalk Server 性能调整](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)  
  
-   [自动进行 BizTalk Server 性能调整](../core/automating-biztalk-server-performance-tuning.md)  
  
## <a name="see-also"></a>请参阅  
 [管理 BizTalk 服务器](../core/use-groups-create-artifacts-optimize-performance-and-more-in-biztalk-server.md)