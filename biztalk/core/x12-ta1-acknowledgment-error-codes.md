---
title: X12 TA1 确认错误代码 |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47eb315f-ec99-4e1e-937b-22199255f14f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2ff9001d73f815b0d62a4e83cc64e1288715f90
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290845"
---
# <a name="x12-ta1-acknowledgment-error-codes"></a>X12 TA1 确认错误代码
本主题列举了 X12 TA1 确认的各个段中所用的错误代码。 有关这些段的详细信息，请参阅[X12 TA1 确认](../core/x12-ta1-acknowledgment.md)。  
  
 下表说明了在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 和 AS2 中支持哪些由 X12 规范指定的错误代码以及不支持哪些错误代码。 引擎行为 (TA104) 的值如下所示：  
  
-   A = 接受  
  
-   E = 已接受但存在错误的交换  
  
-   R = 已拒绝/已挂起的交换  
  
|条件|引擎行为 （TA104 值）|TA105 值|是否支持？|  
|---------------|-------------------------------------|-----------------|----------------|  
|成功|仅当辅助副本配置为使用手动故障转移模式，并且至少一个辅助副本当前与主要副本同步时，|000|是|  
|标头 ISA 13 和尾部 IEA02 的交换控制编号不匹配|E|001|是|  
|不支持 ISA11（控制标准）中的标准|E|002|是<br /><br /> （如果 ID 不匹配）|  
|不支持控件的版本|E|003|不<sup>1</sup>|  
|段终止符无效<sup>2</sup>|R|004|是|  
|发送方的交换 ID 限定符无效|R|005|是<br /><br /> （如果 ID 不匹配）|  
|交换发送方 ID 无效|E|006|是<sup>3</sup>|  
|接收方的交换 ID 限定符无效|R|007|是<br /><br /> （如果 ID 不匹配）|  
|交换接收方 ID 无效|E|008|不<sup>3</sup>|  
|未知交换接收方 ID|E|009|是|  
|授权信息限定符值无效|R|010|是<br /><br /> （如果 ID 不匹配）|  
|授权信息值无效|R|011|是<br /><br /> （如果已对参与方进行配置/赋值）|  
|安全信息限定符值无效|R|012|是<br /><br /> （如果 ID 不匹配）|  
|安全信息值无效|R|013|是<br /><br /> （如果已对参与方进行配置/赋值）|  
|交换日期值无效|R|014|是|  
|交换时间值无效|R|015|是|  
|交换标准标识符值无效|R|016|是|  
|交换版本 ID 值无效|R|017|是<sup>4</sup>|  
|交换控制编号值无效|R|018|是|  
|确认请求值无效|E|019|是|  
|测试指示器值无效|E|020|是|  
|包含的组数值无效|E|021|是|  
|控制结构无效|R|022|是|  
|文件结尾（传输）不正确（过早结束）|R|023|是|  
|交换内容无效（如 GS 段无效）|R|024|是|  
|交换控制编号重复|R<br /><br /> （基于设置）|025|是|  
|数据元素分隔符无效|R|026|是|  
|组件元素分隔符无效|R|027|是|  
|延迟送达请求中的送达日期无效|不支持|-|-|  
|延迟送达请求中的送达时间无效|不支持|-|-|  
|延迟送达请求中的送达时间代码无效|不支持|-|-|  
|服务的级别无效|不支持|-|-|  
  
 <sup>1</sup>错误代码 017 改为使用。  
  
 <sup>2</sup>的段终止符的有效组合： 仅，段终止符 char 和段终止符字符跟后缀 1 和 2 后缀。  
  
 <sup>3</sup>支持如果接收的交换上接收端口要求身份验证。 将检查发送方 ID 的相关属性，如果不一致，将会拒绝。 如果参与方设置因未进行配置而不可用，将拒绝此交换。  
  
 <sup>4</sup>指示枚举值无效。