---
title: 如何查看架构的架构定义 (XSD) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, viewing
- managing [schemas], viewing
- viewing, schema definitions
- schemas, schema definition (XSD)
- managing [schemas], schema definition (XSD)
ms.assetid: 21b6d9e6-5737-4334-9fe6-15ae01f90c0d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 558c87b4ed8d9a5504725c17a7f8d36bb10e821d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985390"
---
# <a name="how-to-view-the-schema-definition-xsd-of-a-schema"></a>如何查看某一架构的架构定义 (XSD)
本主题介绍如何使用 BizTalk Server 管理控制台来查看某一架构的架构定义 (XSD)。 您可能要查看架构定义以排除架构验证错误或验证部署了正确的架构。  
  
## <a name="prerequisites"></a>必要條件  
 若要执行本主题中描述的过程，必须以 BizTalk Server Administrators 组或 BizTalk Server Operators 组成员的帐户身份登录。 有关详细的权限的信息，请参阅[用于部署和管理 BizTalk 应用程序所需权限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-view-the-xsd-of-a-schema"></a>查看架构的 XSD  
  
1. 单击**启动**，单击**所有程序**，单击[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然后单击**BizTalk Server 管理**。  
  
2. 在控制台树中，展开**BizTalk Server 管理**，展开包含你想要查看其 XSD 的架构的 BizTalk 组，然后展开包含该架构的应用程序。  
  
3. 单击**架构**，右键单击该架构，然后单击**属性**。  
  
4. 在左窗格中，单击**架构视图**。  
  
    该 XSD 将显示在右窗格中。  
  
## <a name="see-also"></a>请参阅  
 [管理架构](../core/managing-schemas.md)