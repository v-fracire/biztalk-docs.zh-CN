---
title: 如何部署和取消部署策略及词汇 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, policies
- policies, deploying
- deploying, vocabularies
- policies, undeploying
- vocabularies, deploying
ms.assetid: 9a7e3310-54b7-482c-8210-b4b11fde4c49
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a2c6200f41a4b473175528ac6d2c8ee75c17894
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013062"
---
# <a name="how-to-deploy-and-undeploy-policies-and-vocabularies"></a>如何部署和取消部署策略及词汇
你可以使用规则引擎部署向导来部署策略或取消部署策略。  
  
 在规则引擎部署向导中尝试进行部署时，下拉列表中将只显示已发布的策略版本。 在尝试取消部署时，下拉列表中则只显示已部署的策略版本。  
  
### <a name="to-deploy-or-undeploy-a-policy"></a>部署或取消部署策略  
  
1. 单击**启动**，依次指向**Program Files**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然后单击**业务规则引擎部署向导**。  
  
   > [!NOTE]
   >  在支持用户帐户控制 (UAC) 的系统上，可能需要具有管理权限才能运行该工具。 要执行此操作，右键单击该应用程序，并选择**以管理员身份运行**。  
  
2. 上**规则引擎部署向导**欢迎页上，单击**下一步**。  
  
3. 选择任一**部署策略**或**取消部署策略**，然后单击**下一步**。  
  
4. 从下拉列表中，选择可用的 SQL Server 计算机和数据库，然后依次**下一步**。  
  
   > [!NOTE]
   >  只能部署到所配置的规则存储数据库中。 如果尝试部署到其他数据库，则会出现错误。  
  
5. 从下拉列表中，选择一个策略，然后依次**下一步**。  
  
   > [!NOTE]
   >  在尝试部署时，下拉列表中将只显示已发布的策略版本。 在尝试取消部署时，下拉列表中则只显示已部署的策略版本。  
  
6. 查看服务器、 数据库和策略信息，然后单击**下一步**。  
  
7. 监视部署或取消部署的进度。 完成后，单击**下一步**。  
  
8. 查看部署或取消部署的完成状态，然后单击**完成**。  
  
> [!NOTE]
>  此外可以部署或通过右键单击策略版本，然后单击取消部署策略版本从业务规则编辑器内的**部署**或**Undeploy**。