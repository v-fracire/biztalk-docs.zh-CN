---
title: 如何诊断 SMTP 适配器问题 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eaf39fd8-b662-4b0c-b5e8-1af02cb4f79b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5a1f88d6d096b697f8fceb3c81f8527fa5f7342
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010310"
---
# <a name="how-to-diagnose-problems-with-the-smtp-adapter"></a>如何诊断 SMTP 适配器问题
本部分提供的步骤可帮助您诊断 SMTP 适配器问题。  
  
### <a name="check-the-smtp-log-files-of-the-smtp-server-for-errors"></a>检查 SMTP 服务器的 SMTP 日志文件是否有错误  
  
- 目标 SMTP 服务器日志文件包含的信息可帮助您解决 SMTP 适配器问题。 默认情况下，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 上的 SMTP 日志文件位于下面的目录中：  
  
   <em>%Windir%\\</em>system32\LogFiles\SMTPSVC1\  
  
  > [!NOTE]
  >  *%Windir%* 是 SMTP 服务器上的 Windows 目录的位置的占位符。  
  > 
  > [!NOTE]
  >  默认情况下，SMTP 日志记录在 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 上处于禁用状态。 有关启用 SMTP 日志记录的信息，请参阅 Windows 服务器文档。  
  
## <a name="see-also"></a>请参阅  
 [工具和实用程序用于故障排除](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [SMTP 适配器故障排除](../core/troubleshooting-the-smtp-adapter.md)