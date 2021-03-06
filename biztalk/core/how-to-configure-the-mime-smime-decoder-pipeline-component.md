---
title: 如何配置 MIME-SMIME 解码器管道组件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, attachments
- pipeline components, MIME/SMIME Decoder
- MIME/SMIME Decoder [pipeline component], configuring
- messages, verifying
- messages, decoding
- messages, digital signatures
- messages, security
ms.assetid: bfd44893-f1c3-4524-abc6-f820b8c0ef07
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 355842ad6b985e9bd8152c4de37571fe526505ab
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991086"
---
# <a name="how-to-configure-the-mime-smime-decoder-pipeline-component"></a>如何配置 MIME-SMIME 解码器管道组件
MIME/SMIME 解码器管道组件用于解码和解密 MIME/SMIME 编码的消息和验证签名消息的数字签名。 当外部合作伙伴与 BizTalk Server 之间需要进行安全文档交换时，此组件非常有用。 此组件还可用于接收带附件的消息。  
  
> [!NOTE]
>  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，MIME/SMIME 解码器管道组件将不再支持本机 64 位模式。  这意味着此组件必须运行在 32 位仿真模式进程 (WOW64) 中。  这意味着运行此解码器组件（或其所属的接收管道）的主机实例必须以 32 位仿真模式运行。  请注意此限制对运行在此主机实例中的其他 BizTalk 元素性能（和其他方面）的影响。  
> 
> [!NOTE]
>  MIME/SMIME 解码器组件也用于 POP3 适配器中。  因此，对于运行 POP3 适配器的主机实例，也存在同样的本机 64 位支持限制。  有关 POP3 适配器的信息，请参阅[POP3 适配器](../core/pop3-adapter.md)。  
  
### <a name="to-configure-the-properties-for-the-mimesmime-decoder-pipeline-component"></a>配置 MIME/SMIME 解码器管道组件的属性  
  
1.  将 MIME/SMIME 解码器管道组件拖至接收管道的“解码”阶段。  
  
2.  在属性窗口中**管道组件属性**部分中，执行以下操作。  
  
    |使用此选项|执行的操作|  
    |--------------|----------------|  
    |**允许非 MIME 消息**|将此属性设置为 **，则返回 True**如果希望接收管道能够接收不是 MIME 编码的消息。 如果使用 MIME/SMIME 解码器管道组件的管道接收不同格式的消息，例如 MIME 编码或普通 XML 消息，则应使用此选项。 默认情况下，此属性设置为**False**，含义组件生成一个错误，如果收到非 MIME 编码的消息输入。 **注意：** MIME 解码器扫描传入的消息搜索"Mime-version"标头的第一个 1024 字节。 如果找不到此头部，则消息将被视为非 MIME 消息。 <br /><br /> 默认值： **False**|  
    |**正文部分内容类型**|指示 MIME 部分的内容类型。 与此内容类型的 MIME 部分将成为 BizTalk 消息正文部分。<br /><br /> 默认值： 无|  
    |**正文部分索引**|指示 MIME 部分列表中的基于 1 的索引。 在列表中此索引处的 MIME 部分将成为 BizTalk 消息正文部分。 若要禁用按索引选择正文部分，使用值**0**。<br /><br /> 默认值： **0**|  
    |**检查吊销列表**|将此属性设置为 **，则返回 True**如果你想要检查证书吊销列表中的发件人用于发送到 BizTalk Server 的消息进行签名的证书。 禁用此选项可提高该组件的性能。<br /><br /> 与证书关联的证书吊销列表从远程网站（例如 Verisign.com）下载。 如果 BizTalk Server 无法连接远程网站，则该消息在管道中将失败。<br /><br /> 中**Wcf-custom 传输属性**对话框中，在常规选项卡上，配置终结点地址、 服务标识，并且SOAPAction标头WCF 自定义发送端口。**|  
  
## <a name="see-also"></a>请参阅  
 [MIME-SMIME 解码器管道组件](../core/mime-smime-decoder-pipeline-component.md)   
 [配置本地管道组件](../core/configuring-native-pipeline-components.md)   
 [MIME-SMIME 属性架构和属性](../core/mime-smime-property-schema-and-properties.md)   
 [MIME（BizTalk Server 示例）](../core/mime-biztalk-server-sample.md)