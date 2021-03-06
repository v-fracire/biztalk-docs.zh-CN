---
title: 分发数字证书 |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- digital signatures
- security, digital signatures
ms.assetid: 3e93a405-3c9b-43f5-bbdf-bec25d43eb45
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 486a1f45dc6a570bab6518eef215f4133015ead5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209413"
---
# <a name="distributing-digital-certificates"></a>分发数字证书
用于数字签名的数字证书通常发出并分发给用户工作站的证书颁发机构 (Ca) — 任一外部的商业实体，例如 VeriSign 或在组织中承载的内部 Ca。 使用的数字证书的类型 （加密算法和密码强度） 可能与组织的不同。 [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]可以进行数字签名使用私钥组成和具有数字签名和/或密钥用法属性的加密值的任何证书格式窗体。 此外，证书的用途应设置为客户端身份验证。  
  
 数字证书的主要用途是标识用于该证书进行数字签名文档，以及用于创建的文档数据的加密的单向哈希的用户。 加密哈希数据登录后检测到数据的任何更改 （如果数据已更改，它不会生成相同的哈希）。 数字证书颁发基于域用户帐户和角色 (或[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]域组)，并特定于用户的资产受到[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]身份验证和用户登录机制。 你可以进行数字签名文档，只能通过使用数字证书颁发专门为你基于你[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]域用户帐户。  
  
 SWIFT[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]使用提供的 A4SWIFT FormGenerator 实用程序生成的窗体要求你进行数字签名 （或副署） 窗体时尝试提交到 A4SWIFT 消息修复和新提交消息 (通过[!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)])。 你无法绕过这一需求[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]。 但是，你可以[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]一起删除和写入消息直接到 （假设你具有相应的凭据用于访问 SharePoint Web 文件夹） 的 SharePoint Web 文件夹。 但是，如果消息不包含有效的数字签名，消息修复和新提交立即拒绝该消息作为安全错误。  
  
 消息修复和新提交组件必须有权在消息中使用的数字证书的公钥修复工作流。 若要启用消息修复和新的提交到公钥的访问的证书。 每个用户必须驻留在其他人的存储上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]托管消息修复和新提交业务流程服务的计算机。  
  
> [!NOTE]
>  消息修复和新提交工作流中使用的证书和用户配置消息修复必须由如 VeriSign 或 e 信任受信任的证书颁发机构颁发。  
  
 有关如何设置内部 Ca 的特定信息，请参阅"设置启动证书颁发机构"MSDN 网站上在[http://go.microsoft.com/fwlink/?LinkId=48688](http://go.microsoft.com/fwlink/?LinkId=48688)。