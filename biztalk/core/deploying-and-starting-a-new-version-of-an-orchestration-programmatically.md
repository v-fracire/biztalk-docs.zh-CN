---
title: 部署和以编程方式启动新版本的业务流程的 |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f90025ec-3641-49ef-8918-88238d6ad420
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26887b70a09d4a7af8d41a4385dffda20e964690
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239021"
---
# <a name="deploying-and-starting-a-new-version-of-an-orchestration-programmatically"></a>部署和以编程方式启动的业务流程的新版本
本主题中的代码说明如何快速部署和启动新版本的业务流程。 由于手动操作会花几秒钟来执行，因此手动取消登记业务流程并随后启动新版本的业务流程将导致生成挂起或重复的消息。 通过本主题中说明的编程方法，可以更快速地执行这些操作，从而减小生成挂起和重复消息的可能性；并且可作为单个事务来执行这些操作，以便其中一个操作失败时，这两个业务流程都保持开始时的相同状态。  
  
> [!NOTE]
>  在极少数情况下，当你使用新版本进行更新业务流程在高负载下运行时某些消息可以成为挂起，即使取消登记，并以编程方式登记业务流程。  我们建议后执行这些操作时，你检查挂起的消息队列和恢复任何挂起的消息。  
  
 下面的代码示例说明如何使用浏览器 OM API 取消登记现有的业务流程并启动新版本的业务流程。  
  
```  
using System;  
using Microsoft.BizTalk.ExplorerOM;  
#endregion  
namespace OrchestrationBinding  
{  
class OrchestrationBinding  
{  
static void Main(string[] args)  
{  
            UpdateOrchestration();  
}  
        static public void UpdateOrchestration()  
        {  
            // Create the root object and set the connection string  
            BtsCatalogExplorer catalog = new BtsCatalogExplorer();  
            catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI";  
            string orchestrationAssemblyV1 = "HelloWorld, Version=1.0.0.0, Culture=neutral, PublicKeyToken=99561c477e487f14";  
            string orchestrationAssemblyV2 = "HelloWorld, Version=2.0.0.0, Culture=neutral, PublicKeyToken=99561c477e487f14";  
            string orchestrationName = "Microsoft.Samples.BizTalk.HelloWorld.HelloSchedule";  
            try  
            {  
                BtsAssembly assemblyV1 = FindAssemblyByFullName(catalog.Assemblies, orchestrationAssemblyV1);  
                BtsAssembly assemblyV2 = FindAssemblyByFullName(catalog.Assemblies, orchestrationAssemblyV2);  
                BtsOrchestration orchestrationV1 = assemblyV1.Orchestrations[orchestrationName];  
                BtsOrchestration orchestrationV2 = assemblyV2.Orchestrations[orchestrationName];  
                orchestrationV1.Status = OrchestrationStatus.Unenlisted;  
                orchestrationV2.Status = OrchestrationStatus.Started;  
                // Commit the accumulated changes transactionally  
                catalog.SaveChanges();  
            }  
            catch (Exception e)  
            {  
                catalog.DiscardChanges();  
                throw;  
            }  
        }  
        static BtsAssembly FindAssemblyByFullName(BtsAssemblyCollection assemblies, string fullName)  
        {  
            foreach (BtsAssembly assembly in assemblies)  
            {  
                if (assembly.DisplayName == fullName)  
                    return assembly;  
            }  
            return null;  
        }  
}  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [更新 BizTalk 应用程序](../core/updating-biztalk-applications.md)   
 [如何登记业务流程](../core/how-to-enlist-an-orchestration.md)   
 [如何取消登记业务流程](../core/how-to-unenlist-an-orchestration.md)