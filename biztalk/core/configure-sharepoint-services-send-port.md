---
title: 配置 SharePoint Services 发送端口 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36aadbc2-316f-4e1c-a5a8-b162470acf9e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39e57d8480825a6473edfbeb64ac5922a91281b7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966958"
---
# <a name="configure-sharepoint-services-send-port"></a>配置 SharePoint Services 发送端口
本主题将比较静态发送端口与动态发送端口，并列出创建 [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] 发送端口的步骤。 具体来说：  

 [静态发送端口与动态发送端口](../core/configure-sharepoint-services-send-port.md#BKMK_StaticvsDynamic)  

 [创建静态发送端口](../core/configure-sharepoint-services-send-port.md#BKMK_StaticSend)  

 [创建动态发送端口](../core/configure-sharepoint-services-send-port.md#BKMK_DynamicSend)  

##  <a name="BKMK_StaticvsDynamic"></a> 静态发送端口与动态发送端口  

||静态发送端口|动态发送端口|  
|-|----------------------|-----------------------|  
|将单个发送端口用于不同适配器。|“否”<br /><br /> 当创建静态发送端口时，将需要传输类型。|是<br /><br /> 通常会将动态发送端口添加到业务流程中。 传输类型在业务流程逻辑中配置。|  
|将单个发送端口用于不同发送端口属性（如 URL）。|“否”<br /><br /> 当创建静态发送端口时，必须配置某些适配器属性（如 URL）。|是<br /><br /> 通常会将动态发送端口添加到业务流程中。 属性在业务流程逻辑中配置。|  
|必须使用默认发送处理程序。|“否”<br /><br /> 可在创建发送端口时配置发送处理程序。|“否”<br /><br /> 可在创建发送端口时配置发送处理程序。|  
|在不知道应将消息发送到何处时使用。|“否”<br /><br /> 在创建静态发送端口时指定传输类型和结束位置。|是<br /><br /> 可以在业务流程和基于内容的路由方案中配置结束位置。 还可以使用规则来筛选消息的发送位置。|  
|将单个发送端口用于向多个合作伙伴发送消息。|“否”<br /><br /> 在创建静态发送端口时指定传输类型和结束位置。|是<br /><br /> 通常会将动态发送端口添加到业务流程中。 属性将在业务流程逻辑中基于你指定的规则配置，可以将消息发送到多个合作伙伴。|  

##  <a name="BKMK_StaticSend"></a> 创建静态发送端口  
 创建静态发送端口时，发送端口使用与传输类型关联的默认发送处理程序。 使用时[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]适配器，发送处理程序的默认**BizTalkServerApplication**。 对于要添加新的发送处理程序的步骤，请转到[如何创建适配器处理程序](http://go.microsoft.com/fwlink/p/?LinkId=263646)。  

 创建静态发送端口：  

1. 在中**BizTalk Server 管理**控制台中，展开**BizTalk 组 [*GroupName*]**，展开**应用程序**，然后展开要包含发送端口的应用程序。  

2. 右键单击**发送端口**，单击**新建**，然后单击**静态单向发送端口**。  

   > [!IMPORTANT]
   >  一个**静态要求响应发送端口**不是可配置为[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]适配器。  

3. 在中**属性**，单击**Windows SharePoint Services**中**类型**下拉列表。 输入**名称**，**发送处理程序**，并**发送管道**属性。  

4. 单击**配置**。 在中**属性**，配置以下各项：  


   |                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   |-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |      适配器 Web Services 端口       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           **所需**。 在 IIS 网站上配置的托管 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 适配器 Web Services 的端口。<br /><br /> 默认端口为端口**80**，这是标准 HTTP 端口。 如果使用除 80 以外的端口，请更新此值。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   |               超时               |                                                                                                                                                                                                                                                                                                                                                                                                                     **所需**。 单位为毫秒，此值用于确定适配器从 Web 服务收到响应的时间。<br /><br /> 默认值是**100000 毫秒**（100 秒）。<br /><br /> 如果消息或批大小大于预期值，请增大此值。<br /><br /> 对 Windows SharePoint Services 适配器 Web Services 进行的适配器运行时 Web Services 调用的超时值（以毫秒计）。 如果消息或批的大小超过适配器预期的平均大小，则可能需要增加此值。                                                                                                                                                                                                                                                                                                                                                                                                                     |
   |            使用客户端 OM            |                                                                                                                                                                                                         **所需**。 确定是使用 SharePoint 客户端对象模型 (CSOM) 还是服务端对象模型 (SSOM)。<br /><br /> 默认值是**是**。 设置为**是**上使用 SharePoint CSOM [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 对 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 计算机没有任何要求。<br /><br /> 设置为**否**若要使用 SharePoint SSOM，包括 web 服务上安装[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]计算机。<br /><br /> [附录 b： 安装 Microsoft SharePoint 适配器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)上使用的 SSOM 和 CSOM 组件提供的特定信息[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]适配器。                                                                                                                                                                                                         |
   |       目标文件夹 URL        |                                                                                                                                                                                                                                                                                                                                                               **所需**。 用于存储文档的 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 文件夹 URL。 输入 SharePoint 站点的相对路径。 例如， **Shared Documents**或**Shared Documents/Purchase Orders /**。 也可以将列表用作目标。 例如， **Lists/Tasks**。 如果指定列表，消息正文则不会和列表项一起保存。 从消息中提取的值将提升到 SharePoint 列中。 **注意：** SharePoint 文档库或文件夹 URL 可以与其名称不同。 查看 Web 浏览器中的地址以获取正确的 URL。                                                                                                                                                                                                                                                                                                                                                                |
   |              Filename               |                                                                                                                                                                                                                                            **可选**。 输入 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 文件名的名称。<br /><br /> 输入文件名称，如**PurchaseOrder0001.xml**或表达式。 表达式包括文本、宏和 XPATH 查询的任意组合。 例如，输入**PurchOrd-%XPATH=//po:PurchaseOrderId%-%MessageID%.xml**。 如果未提供文件名，则使用原始文件的文件名、业务流程提供的值或“Msg-%MessageID%.xml”。 请参阅[Windows SharePoint Services 适配器表达式](../core/windows-sharepoint-services-adapter-expressions.md)有关详细信息。 **注意：** 时向列表发送消息，此文件名值被忽略，不会保存在 SharePoint 列。 相反，更新标题列使用其中一个可用的 16 列。 SharePoint 列表不具有“文件名”栏。                                                                                                                                                                                                                                             |
   |         命名空间别名          |                                                                                                                                                                                                                                                                                                                                                                                                           **可选**。 以逗号或分号分隔的命名空间别名定义列表。<br /><br /> 使用此字段可以定义在“文件名”或“栏值”等字段中引入的 XPATH 查询所使用的命名空间别名。 例如，输入**po ='<http://OrderProcess/POrder>'，conf ='<http://OrderProcess/Confirmation>' xmlns =""; ipsol = {D8217CF1-4EF7-4bb5-A30D-765ECB09E0D9}**。 **注意：** 此属性不会覆盖 WSS。业务流程定义 ConfigNamespacesAliases 消息上下文属性。 相反，将合并两个值。                                                                                                                                                                                                                                                                                                                                                                                                           |
   |              Overwrite              |                                                                                                                                                                                                                                                                                                                                    **所需**。 如果存在某个文件，则确定是否覆盖该文件。<br /><br /> 默认值是**否**。 选项包括：<br /><br /> -   **不**： 引发错误并挂起该消息，如果存在具有相同名称的文件。<br />-   **业务流程**： 使用定义业务流程中，如果存在具有相同名称的文件的值。<br />-   **重命名**： 重命名新文件，如果存在具有相同名称的文件。<br />-   **是**： 如果具有相同的名称，则覆盖现有文件。<br />     如果设置为**是**，发送大量同名消息可能会导致 SharePoint 事件查看器错误。 这些错误不会对适配器造成影响，且任何失败的消息都会重试。                                                                                                                                                                                                                                                                                                                                     |
   |         SharePoint 站点 URL         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     **所需**。 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 网站的完整 URL。 例如，http://<em>SharePointServer</em>/sites/testsite。 **注意：** 一个发送端口或接收位置的 URI 不能超过 256 个字符。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |    Microsoft Office 集成     |                                       **所需**。 对于二进制消息，必须使用**否**或**可选**。<br /><br /> 默认值是**可选**。 选项包括：<br /><br /> <ul><li>**否**： 将文档保存**作为-是**。 二进制消息可以使用此选项。</li><li>**可选**： 修改文档，使其自动在 InfoPath 等 Office 应用程序中打开。 如果找不到处理指令，处理文档**为-是**。 二进制消息可以使用此选项。</li><li>**业务流程**： 使用业务流程中定义的值。</li><li>**是**： 修改文档，使其自动在 InfoPath 等 Office 应用程序中打开。 如果找不到处理指令，则会挂起消息。<br /><br />     如果设置为**是**，则需要至少以下属性对之一：<br /><br /> <ul><li>*模板文档库*和*模板 Namespace 列*</li><li>*模板后备文档库*和*模板回退 Namespace 列*</li></ul></li><li>**是 （InfoPath 表单库）**： 如果 InfoPath 解决方案位于表单库，则修改文档，使它在 InfoPath 等 Office 应用程序中自动打开。 如果表单库不包含解决方案，则会挂起消息。</li></ul>                                       |
   |     模板文档库      |                                                                                                                                                                                                                                                **所需*仅*时*模板 Namespace 列*填充**。 存储 InfoPath 解决方案的 SharePoint 文档库。 例如， **My Solutions**。 适配器会*模板文档库*匹配的 InfoPath 解决方案。 如果找不到一种解决方案，适配器会*模板后备文档库*。 **注意：** *模板文档库*要求至少一个 Single line of text SharePoint 栏的填充以下： <ul><li>命名空间和用 InfoPath 解决方案打开的 XML 文档的根节点</li><li>或者 XML 文档的根节点</li></ul> 有关详细信息，请参阅[演练： 模块 2-将 Office 与 Windows SharePoint Services 适配器相集成](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)。                                                                                                                                                                                                                                                 |
   | 模板后备文档库 | **所需*仅*时*模板后备 Namespace 栏*填充**。 存储 InfoPath 解决方案的 SharePoint 文档库。 例如，**模板**。<br /><br /> 如果在找不到一种解决方案*模板文档库*，适配器会*模板后备文档库*匹配的 InfoPath 解决方案。 *模板后备文档库*并*模板文档库*字段可用于两组 InfoPath 解决方案。 InfoPath 解决方案包括适合于所有通用目的的通用 InfoPath 解决方案，以及只用于特定合作伙伴的专用 InfoPath 解决方案。 *模板后备文档库*字段应指向通用解决方案，并*模板文档库*应指向该特定合作伙伴的专用解决方案。 **注意：***模板后备文档库*要求至少一个 Single line of text SharePoint 栏的填充以下：   <ul><li>命名空间和用 InfoPath 解决方案打开的 XML 文档的根节点</li><li>或者 XML 文档的根节点</li></ul> 有关详细信息，请参阅[演练： 模块 2-将 Office 与 Windows SharePoint Services 适配器相集成](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)。 |
   | 模板后备命名空间栏 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         **所需*仅*时*模板后备文档库*填充**。 存储 InfoPath 解决方案的命名空间的 SharePoint 文档库。 例如， **myNamespace**。 **注意：** 此字段是区分大小写。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |     模板命名空间栏      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    **所需*仅*时*模板文档库*填充**。 SharePoint*模板文档库*存储 InfoPath 解决方案命名空间的列。 例如， **myNamespace**。 **注意：** 此字段是区分大小写。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
   |     SharePoint Online 密码      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              **可选**。 SharePoint Online 帐户的密码。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |     SharePoint Online 用户名      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              **可选**。 SharePoint Online 帐户的用户名。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |             列 `n`              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        **可选**。 中存在的 SharePoint 栏*目标文档库*。 使用从消息中提取或中指定的值更新该列*列值*字段。 **注意：** 可以指定最多 16 个列。 此字段区分大小写。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |          列 `n` 值           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        **可选**。 输入要为此消息设置的栏值。 你可以键入文本值（例如“Purchase Order”），也可以键入表达式。 表达式可以包括文本、宏和 XPATH 查询的任意组合。 例如，输入 **"%xpath=//po:poamount%"、"%sendingorchestrationid%"**。 **注意：** 可以指定最多 16 个列。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |


5. 单击**确定**保存设置。  

6. 其他发送端口配置选项包括：  

   1.  [如何为发送端口配置传输高级选项](../core/how-to-configure-transport-advanced-options-for-a-send-port.md)  

   2.  [如何为发送端口配置备份传输选项](../core/how-to-configure-backup-transport-options-for-a-send-port.md)  

   3.  [如何配置发送端口的出站映射](../core/how-to-configure-outbound-maps-for-a-send-port.md)  

   4.  [如何为发送端口配置筛选器](../core/how-to-configure-filters-for-a-send-port.md)  

   5.  [如何为发送端口分配证书](../core/how-to-assign-a-certificate-to-a-send-port.md)  

   6.  [如何为发送端口配置跟踪](../core/how-to-configure-tracking-for-a-send-port.md)  

##  <a name="BKMK_DynamicSend"></a> 创建动态发送端口  
 创建动态发送端口时，可以为每个适配器配置发送处理程序。 多个适配器可以使用单个动态发送端口。 请参阅[动态发送端口处理程序是可配置](../core/dynamic-send-port-handler-is-configurable.md)有关配置动态发送端口处理程序的步骤。  

1. 在中**BizTalk Server 管理**控制台中，展开**BizTalk 组 [*GroupName*]**，展开**应用程序**，然后展开要包含发送端口的应用程序。  

2. 右键单击**发送端口**，单击**新建**，然后选择**动态单向发送端口**或**动态要求响应发送端口**  

3. 在中**属性**，输入**名称**并**管道**属性  

    单击**配置**。  

4. 在中**配置发送处理程序**窗口中，选择**发送处理程序**适用于单个适配器。 默认发送处理程序是**BizTalkServerApplication**。 对于要添加新的发送处理程序的步骤，请转到[如何创建适配器处理程序](http://go.microsoft.com/fwlink/p/?LinkId=263646)。  

    使用单独的主机出于许多原因，其中包括：  

   - **32 位要求**： 某些适配器需要 32 位主机，如 FTP 和 POP3 适配器。 你可以将所有或各个 32 位适配器分到它们自己的主机组中。  

      [BizTalk Server 64 位支持](../core/biztalk-server-64-bit-support2.md)  

   - **按用途划分主机**： 创建用于发送主机、 主机用于接收、 处理业务流程的主机和一个主机用于跟踪。  

   - **不同的主机设置**： 在主机级别实施了许多设置。 因此，可以为每个主机配置不同的阻止设置。 例如，你可以在 HostA 上禁用阻止。 跟踪 HostB 中的每个事件。 修改 HostC 的 .NET CLR 设置。 增加 HostD 的内存使用率。  

   - **安全**： 在主机级别实施安全性。 每个主机在各自的 Windows 帐户下运行。 例如，HostA 使用 FILE 适配器来访问文件共享。 向 HostA 授予文件共享的用户帐户权限。 HostB 使用 IIS 服务器上托管的 Web 服务。 向 HostB 授予针对该 Web 服务的用户帐户权限。 这同时也会阻止其他主机帐户访问不需要访问的实体。  

   - **单独的适配器**： 例如，你有多个项目 （接收位置和发送端口） 使用 HTTP 适配器。 你希望与该 HTTP 适配器关联的一切内容位于自己的主机中。  

   - **单独的业务流程**： 个体业务流程可以在它们自己的主机。 例如，如果某个业务流程的内存或 CPU 使用率较高，则将该业务流程置于自己的主机中。  

     [BizTalk Server 性能优化指南](http://msdn.microsoft.com/library/dn775063\(v=bts.10\).aspx)并[如何维护和故障排除 BizTalk Server 数据库](http://support.microsoft.com/kb/952555)提供了性能建议。  

5. 单击**确定**保存设置。  

6. 其他发送端口配置选项包括：  

   1.  [如何为发送端口配置传输高级选项](../core/how-to-configure-transport-advanced-options-for-a-send-port.md)  

   2.  [如何配置发送端口的出站映射](../core/how-to-configure-outbound-maps-for-a-send-port.md)  

   3.  [如何为发送端口配置筛选器](../core/how-to-configure-filters-for-a-send-port.md)  

   4.  [如何为发送端口分配证书](../core/how-to-assign-a-certificate-to-a-send-port.md)  

   5.  [如何为发送端口配置跟踪](../core/how-to-configure-tracking-for-a-send-port.md)  

7. 单击**确定**保存设置。  

   其他发送端口主题：  

   [创建和配置发送端口](../core/creating-and-configuring-send-ports.md)  

   [创建和配置发送端口组](../core/creating-and-configuring-send-port-groups.md)  

## <a name="see-also"></a>请参阅  
 [SharePoint Services 适配器故障排除](../core/troubleshooting-sharepoint-services-adapter.md)   
 [配置 SharePoint Services 接收位置](../core/configure-sharepoint-services-receive-location.md)   
 [CSOM：SharePoint Services 适配器](../core/csom-sharepoint-services-adapter.md)