---
title: AddResource 命令： BAM 项目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9de7a82-9b06-4d50-9678-73140e80d0af
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abbd1e76204db4e642f0bd17e09b1d6f4b8b1773
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004110"
---
# <a name="addresource-command-bam-artifact"></a>AddResource 命令：BAM 项目
若要将 BAM 项目添加到 BizTalk 应用程序，请使用**AddResource**命令并指定**system.biztalk: bam**类型参数。 运行此命令可将 BAM 项目文件添加到 BizTalk 管理数据库中。 该 BAM 项目还会显示在 BizTalk Server 管理控制台中，即它所添加到的应用程序的“资源”文件夹下。 此外，当您使用列出该文件[ListApp 命令](../core/listapp-command.md)。  
  
 使用 AddResource 命令添加 BAM 定义不会部署 BAM 定义。 而是在使用导入向导将包含 BAM 定义的 .msi 文件导入应用程序中时，BAM 定义才会部署到本地计算机。  
  
## <a name="usage"></a>用法  
 **BTSTask AddResource** [**/ApplicationName:**<em>值</em>] **/Type:System.BizTalk:Bam**[**/overwrite**] **/Source:**<em>值</em>[**/Destination:**<em>值</em>] [**/Server:** <em>值</em>] [**/database:**<em>值</em>]  
  
## <a name="parameters"></a>Parameters  
  
|参数|Required|ReplTest1|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或 **/A**，请参阅备注)|“否”|向其添加 BAM 项目的 BizTalk 应用程序的名称。 如果名称包含空格，则必须将其括在双引号 （"）。 如果未指定应用程序名称，则使用组的默认 BizTalk 应用程序。|  
|**/ 键入**(或 **/T**，请参阅备注)|是|**System.biztalk: bam** （此值不区分大小写。）|  
|**/ 覆盖**(或 **/O**，请参阅备注)|“否”|更新现有 BAM 项目的选项。 如果未指定，且应用程序中已经存在与要添加的 BAM 项目名称相同的项目，则 AddResource 操作将失败。|  
|**/Source** (或 **/So**，请参阅备注)|是|BAM 项目文件的完整路径，包含文件名。 如果路径包含空格，则必须将其括在双引号 （"）。|  
|**/ 目标**(或**De**，请参阅备注)|“否”|从 .msi 文件安装应用程序时，BAM 项目文件要复制到的位置的完整路径。 如果未提供，该文件是期间不会复制到本地文件系统安装。 如果路径包含空格，则必须将其括在双引号 （"）。|  
|**/ 服务器**(或 **/Se**，请参阅备注)|“否”|BizTalk 管理数据库的宿主 SQL Server 实例的名称，格式为“服务器名称\实例名称,端口”。<br /><br /> 只在实例名称与服务器名称不相同时才需要指定实例名称。 只在 SQL Server 不使用默认端口号 (1433) 时才需要指定端口。<br /><br /> 示例：<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果未提供，则使用本地计算机上运行的 SQL Server 实例的名称。|  
|**/ 数据库**(或 **/Da**，请参阅备注)|“否”|BizTalk 管理数据库的名称。 如果未提供，则使用在本地 SQL Server 实例中运行的 BizTalk 管理数据库。|  
  
## <a name="sample"></a>示例  
 **BTSTask AddResource /ApplicationName:MyApplication /Type: system.biztalk: bam / 覆盖 /Source:"C:\Source BAMfiles\MyBAMfile.xml"/Destination:"C:\New BAMfiles\MyBAMfile.xml"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## <a name="remarks"></a>Remarks  
 参数不区分大小写。 指定参数无需键入整个参数名，只需键入可明确标识该参数的参数名的前几个字母即可。  
  
## <a name="see-also"></a>请参阅  
 [AddResource 命令](../core/addresource-command.md)   
 [如何向应用程序添加 BAM 项目](../core/how-to-add-a-bam-artifact-to-an-application.md)