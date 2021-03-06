---
title: 清单： 存档和清除 BizTalk 跟踪数据库 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- archiving [Tracking database], checklist
- checklists, purging [Tracking database]
- purging, checklist
- checklists, archiving [Tracking database]
ms.assetid: dccbf471-2add-498e-b292-287d9a94161b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59a162d56badd7df7f49ceadc6abc3832dd50806
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971014"
---
# <a name="checklist-archiving-and-purging-the-biztalk-tracking-database"></a>清单： 存档和清除 BizTalk 跟踪数据库

|步骤|参考|  
|----------|---------------|  
|阅读存档和清除概述，以便进一步熟悉存档和清除跟踪数据的过程。|[存档和清除 BizTalk 跟踪数据库](../core/archiving-and-purging-the-biztalk-tracking-database.md)|  
|尽管可以使用您的登录凭据来运行 DTA 清除和存档作业，但为了提高安全性，应该配置具有所需 SQL Server 凭据的 BTS_BACKUP_USERS 角色来运行 DTA 清除和存档作业。 这样有助于防止特权提升。|[如何配置 BTS_BACKUP_USERS 角色以存档和清除 BizTalk 跟踪数据库中的数据](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)|  
|配置 DTA 清除和存档作业。|[如何配置 DTA 清除和存档作业](../core/how-to-configure-the-dta-purge-and-archive-job.md)|  
|运行 DTA 清除和存档作业，该作业会将数据存档到 BizTalk 跟踪 (BizTalkDTADb) 数据库中并清除旧的数据。|[如何从 BizTalk 跟踪数据库中清除数据](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)|  
|另外，可以从 BizTalk 跟踪 (BizTalkDTADb) 数据库中手动清除数据。|[如何从 BizTalk 跟踪数据库中手动清除数据](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)|  
|对 BizTalk 跟踪 (BizTalkDTADb) 数据库中的存档数据启用自动验证。|[如何启用自动存档验证](../core/how-to-enable-automatic-archive-validation.md)|  
|将跟踪的消息复制到 BizTalk 跟踪 (BizTalkDTADb) 数据库中。 使用 DTA 清除和存档作业清除数据时，要求进行此操作。|[如何将跟踪的消息复制到 BizTalk 跟踪数据库](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)|  

## <a name="see-also"></a>请参阅  
 [存档和清除 BizTalk 跟踪数据库](../core/archiving-and-purging-the-biztalk-tracking-database.md)