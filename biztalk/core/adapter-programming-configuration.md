---
title: 适配器编程配置 |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e5fef6c-6928-42e7-9a1f-42b5bd769937
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e908b3ac79970b917e1e7964868b3b9d5bd852d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229981"
---
# <a name="adapter-programming-configuration"></a>适配器编程配置
每一种类型的密码同步适配器都有不同的配置要求，具体取决于设计适配器所针对的非 Windows 系统。 与关联应用程序一样，您可以使用企业单一登录配置存储更安全地集中存储配置属性。  
  
 与使用其他配置存储应用程序一样，管理员可以使用企业单一登录管理用户界面来查找和读取描述适配器配置属性的 XML 文件。 管理工具使用 XML 文件呈现属性页，以便为指定的适配器收集所需的属性值。 您还可使用 ISSOConfigStore 向配置存储加载或从中读取 XML 名称/值组合，或使用 SSOPS 工具。  
  
 还可以使用企业单一登录管理工具来启用或禁用适配器。 在初始创建时，适配器处于禁用状态。  
  
## <a name="see-also"></a>另请参阅  
 [密码同步适配器](../core/password-sync-adapters.md)