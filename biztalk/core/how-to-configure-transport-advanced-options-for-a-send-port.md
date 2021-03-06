---
title: 如何配置传输高级选项的发送端口 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, transport options [send ports]
- configuring, send ports
- send ports, transport options
- managing [send ports], configuring
- managing [send ports], transport options
ms.assetid: b0033e09-3c18-4e53-a470-e12978e61ba1
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3aada2fa4f32e66c88f295e96bd71a9330cfb988
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023875"
---
# <a name="how-to-configure-transport-advanced-options-for-a-send-port"></a>如何为发送端口配置传输高级选项
使用 BizTalk Server 管理控制台来配置传输高级选项的发送端口。 这些选项决定发送端口处理消息的方式，如发送消息失败时的重试次数以及该端口的服务时段计划。  
  
> [!NOTE]
> **从开始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，可以启用按序的送达的动态发送端口，具体取决于相应适配器类型。 此选项才可用的适配器类型对于静态发送端口，如文件适配器或 FTP 适配器能保证按序的送达的位置。
> 
> 请考虑六个消息： M1、 M2、 M3、 M4、 M5，和 M6。 M1，M3，M5 意为文件位置。 M2、 M4 和 M6 用于 FTP。 按序的送达动态发送端口可确保，M1、 M3 和 M5 进行排序;和 M2、 M4 和 M6 分别进行排序。 
> 
> 对于这些不支持按序的送达的适配器类型，不存在任何可配置的动态发送端口属性。 在运行时自动确定其传输选项。  
> 
> **对于以前的 BizTalk 版本**使用动态端口，没有可用于配置，因为在运行时自动确定传输选项的任何属性。

  
## <a name="prerequisites"></a>必要條件  
 若要执行本主题中的过程，必须是 BizTalk Server Administrators 组的成员的帐户登录。 有关详细的权限的信息，请参阅[用于部署和管理 BizTalk 应用程序所需权限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="controlling-send-port-priority"></a>控制发送端口的优先级  
 “传输高级选项”的“优先级”设置控制从消息框中删除消息的顺序。 较高优先级的端口会比较低优先级的端口更早地得到处理，从而使较高优先级的端口比单一主机内的其他发送端口更为重要。  
  
 当某些类型的请求要求响应时间较短时，优先级很有用。 例如，有多个发送端口连接到不同的系统，用于处理正常请求和交互式请求。 交互式请求要求响应时间短，因此，在提交交互式请求时，需确保尽快对其进行处理。  
  
 BizTalk Server 在处理 MessageBox 中具有不同优先级的消息时，不会公平对待各个消息。 如果处理开始时 MessageBox 中有数量相等但优先级不同的两种项目，则只有在处理完所有高优先级的项目后，才会处理较低优先级的项目。 如果高优先级的项目数量巨大，则有可能永远也不会处理较低优先级的项目。 换句话说，较低优先级的项目将会遇到资源不足的情况。  
  
> [!WARNING]
>  为了尽量降低消息资源不足的危险，应在实际负载下彻底测试应用程序，以确保可以处理所有消息。 如果不对解决方案进行测试，则有可能出现消息得不到处理的情况。  
  
 BizTalk Server 会在内部为每个订阅分配一个优先级。 优先级可以是从 1（最高优先级）到 10（最低优先级）的任意数字。 由于激活订阅的默认优先级为 7，而相关订阅的默认优先级为 5，因此，相关消息会比激活订阅更先传送。  
  
## <a name="configure-the-transport-options"></a>配置传输选项 
  
1.  打开 **“BizTalk Server 管理”**。  
  
2.  展开 BizTalk 组，然后展开 BizTalk 应用程序。  
  
3.  选择**发送端口**，右键单击发送端口以配置，然后选择**属性**。  
  
4.  在左窗格中，选择**传输高级选项**。  
  
5.  下表中所述配置传输选项，然后选择**确定**。  仅以下属性中的一些适用于动态发送端口。
  
    |使用此选项|执行的操作|  
    |--------------|----------------|  
    |**重试次数**|指定在消息失败时发送端口重发消息的次数。 默认值为 3;允许的范围是从 0 到 1000。|  
    |**重试间隔**|指定两次重发消息尝试之间的时间间隔（以分钟为单位）。 默认值为 5;允许的范围是从 0 到 525600。|  
    |**Priority**|设置重发尝试的优先级。|  
    |**按序的送达**|选中此复选框将按接收顺序发送消息。|  
    |**停止发送随后的消息当前消息失败**|选中此复选框将停止发送失败消息后面的消息。 此选项是时才可用**按序送达**选择选项。|  
    |**为失败消息启用路由功能**|选中此选项将为失败消息启用路由功能。|  
    |**启用服务时段**|选中此选项并指定开始时间和停止时间，即可指定发送端口每天运行的时间段。|  
    |**开始时间**|指定发送端口每天开始发送消息的时间。 此选项是时才可用**启用服务时段**选择选项。|  
    |**停止时间**|指定发送端口每天停止发送消息的时间。 此选项是时才可用**启用服务时段**选择选项。|  
  
## <a name="see-also"></a>请参阅  
[消息按序送达](../core/ordered-delivery-of-messages.md)  
 [创建和配置发送端口](../core/creating-and-configuring-send-ports.md)