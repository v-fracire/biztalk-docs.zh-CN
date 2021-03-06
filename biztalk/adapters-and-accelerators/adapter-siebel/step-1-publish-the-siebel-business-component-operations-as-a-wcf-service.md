---
title: 步骤 1： 将 Siebel 业务组件操作作为 WCF 服务发布 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acfa0c36-50f1-45c1-9fc2-e5e5cedaa6a0
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 800e9789eca1121abd37de4df92e9d5e735802f3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983014"
---
# <a name="step-1-publish-the-siebel-business-component-operations-as-a-wcf-service"></a>步骤 1： 将 Siebel 业务组件操作发布为 WCF 服务
![步骤 1，共 4 步](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **完成时间：** 10 分钟  
  
 **目标：** 可以使用 WCF 适配器服务开发向导在如 Internet 信息服务 (IIS) 或 Windows 进程激活服务 (WAS) 宿主环境中生成可承载的 WCF 服务。 本主题演示如何使用向导生成的 WCF 服务文件。  
  
## <a name="prerequisites"></a>必要條件  
 运行向导之前，安装以下组件：  
  
- [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] 使用**完成**选项或**自定义**选项 (，然后选择**工具**中此选项)。 这为 WCF 适配器服务开发向导将安装 Visual Studio 模板。  
  
- [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]  
  
- 所需的 Siebel 客户端。  
  
  有关这些先决条件的详细信息，请参阅[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安装指南。 安装指南通常安装在\<安装驱动器\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。  
  
## <a name="publish-the-siebel-business-components-as-a-wcf-service"></a>将 Siebel 业务组件发布为 WCF 服务  
  
1. 启动[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，然后创建一个项目。  
  
2. 在中**新的项目**对话框中，从**项目类型**窗格中，选择**Visual C#**。 从**模板**窗格中，选择**WCF 适配器服务**。  
  
    或者，从**项目类型**窗格中，展开**Visual C#**，然后选择**Web**。 从**模板**窗格中，选择**WCF 适配器服务**。  
  
   > [!NOTE]
   >  如果使用 Web 开发组件，安装 Visual Studio **WCF 适配器服务**模板也会提供**新的网站**选项。  
  
3. 指定的名称和位置的解决方案，然后单击**确定**。 WCF 适配器服务开发向导启动。  
  
4. 在欢迎页上，单击**下一步**。  
  
5. 在选择操作页上指定要连接到 Siebel 系统的连接字符串。 为此：  
  
   1. 在中**选择绑定**列表中，单击**siebelBinding**，然后单击**配置**。  
  
   2. 在中**配置适配器**对话框中，单击**安全**选项卡。  
  
   3. 在中**客户端凭据类型**列表中，选择**用户名**，然后指定用户名和密码以连接到 Siebel 系统。  
  
   4. 单击**URI 属性**选项卡，然后指定连接参数的值。 有关详细信息的连接 URI 对于[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，请参阅[Creat Siebel 系统连接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。  
  
      > [!NOTE]
      >  如果连接参数包含任何保留的字符 （如 XML 特殊字符），则必须指定其作为-处于**URI 属性**选项卡上，即，而无需使用任何转义符。 但是，如果指定的 URI 中直接**配置 URI**字段和连接参数包含保留的字符，则必须指定连接参数使用正确的转义字符。  
  
   5. 单击**绑定属性**选项卡上，并且如果你想要针对的操作所需任何操作，然后指定绑定属性的值。  
  
       有关绑定属性的详细信息，请参阅[了解关于 BizTalk Adapter for Siebel 绑定属性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  
  
   6. 单击**确定**，然后单击**Connect**。 建立连接后，连接状态显示为**已连接**。  
  
6. 在选择操作页中**选择协定类型**列表中，单击**客户端 （出站操作）**。  
  
7. 在中**选择一个类别**框中，展开 Siebel**业务对象**节点以查看 Siebel 存储库中的业务对象的列表。 此示例中，请执行以下操作：  
  
   1.  展开**帐户**业务对象，然后单击**帐户**业务组件。  
  
   2.  在中**可用类别和操作**框中，选择**查询**操作，并单击**添加**。 所选的操作列入**添加的类别和操作**框。  
  
        ![选择 Siebel 业务组件操作](../../adapters-and-accelerators/adapter-siebel/media/ed0cb649-dc4d-49ce-9541-c491c9cc9ac9.gif "ed0cb649-dc4d-49ce-9541-c491c9cc9ac9")  
  
8. 在选择操作页上单击**下一步**。  
  
9. 在配置服务和终结点行为页上，指定值以配置的服务和终结点行为。  
  
   1. 在中**服务行为配置**框中，指定以下设置的值：  
  
      |属性|指定的值|  
      |----------------------|-----------------------|  
      |EnableMetadataExchange|将此设置为 **，则返回 True**创建元数据交换终结点。 通过此选项设置为 **，则返回 True**，使服务元数据可使用标准的协议，如 WS-元数据交换 (MEX) 和 HTTP/GET 请求。<br /><br /> 默认值是**False**。|  
      |IncludeExceptionDetailsinFault|将此设置为 **，则返回 True**返回到客户端以便进行调试的 SOAP 错误的详细信息中包含托管的异常信息。 默认值是**False**。|  
      |“属性”|服务行为配置名称。|  
      |UseServiceCertificate|指定是否想要使用的 WCF 消息级别安全模式。 默认值是 **，则返回 True**。<br /><br /> 对于本教程，必须将其设置**False**。|  
      |FindValue|一个字符串，指定要在 X.509 证书存储区中搜索的值。<br /><br /> **注意：** 为此属性仅当指定值**UseServiceCertificate**设置为**True**。|  
      |StoreLocation|一个值，指定该服务可用于验证的客户端证书的证书存储区位置。<br /><br /> **注意：** 为此属性仅当指定值**UseServiceCertificate**设置为**True**。|  
      |StoreName|要打开的 X.509 证书存储的名称。<br /><br /> **注意：** 为此属性仅当指定值**UseServiceCertificate**设置为**True**。|  
      |X509FindType|要执行的 X.509 搜索的类型。<br /><br /> **注意：** 为此属性仅当指定值**UseServiceCertificate**设置为**True**。|  
  
      > [!NOTE]
      >  有关证书和关联的属性的详细信息，请参阅[X509ClientCertificateCredentialsElement 属性](https://msdn.microsoft.com/library/system.servicemodel.configuration.x509clientcertificatecredentialselement_properties.aspx)。
  
   2. 在中**终结点行为配置**框中，指定以下设置的值：  
  
      |属性|指定的值|  
      |----------------------|-----------------------|  
      |身份验证类型|-将此设置为**ClientCredentialUserNamePassword**使客户端可以使用 WCF 服务时指定的用户名和密码。<br /><br /> -将此设置为**HTTPUserNamePassword**若要启用客户端的 HTTP 标头的一部分指定用户名和密码。<br /><br /> -将此设置为**自动**首先使客户端可以指定通过凭据**ClientCredential**接口。 如果此操作失败，客户端可以将作为 HTTP 标头的一部分传递的凭据。<br /><br /> 默认值是**自动**。对于 Microsoft Office SharePoint Server 使用 WCF 服务，应设置为**HTTPUserNamePassword**。|  
      |“属性”|指定的终结点行为配置名称。|  
      |UsernameHeader|用户名称标头的名称。 对于此示例中，指定**MyUserHeader**。 有关 HTTP 标头的详细信息，请参阅"支持的自定义 HTTP 和 SOAP 标头"网址[ http://go.microsoft.com/fwlink/?LinkId=106692 ](http://go.microsoft.com/fwlink/?LinkId=106692)。<br /><br /> **注意：** 必须指定此属性的值，如果**身份验证类型**设置为**HTTPUserNamePassword**。 如果**身份验证类型**设置为**自动**，此为可选属性。|  
      |PasswordHeader|密码标头的名称。 对于此示例中，指定**MyPassHeader**。 有关 HTTP 标头的详细信息，请参阅"支持的自定义 HTTP 和 SOAP 标头"网址[ http://go.microsoft.com/fwlink/?LinkId=106692 ](http://go.microsoft.com/fwlink/?LinkId=106692)。<br /><br /> **注意：** 必须指定此属性的值，如果**身份验证类型**设置为**HTTPUserNamePassword**。 如果**身份验证类型**设置为**自动**，此为可选属性。|  
  
      下图显示了具有指定值的配置服务和终结点行为页。  
  
      ![配置服务和终结点行为页](../../adapters-and-accelerators/adapter-sap/media/0a286b0c-7f0d-46c5-9b56-29bef3a1deea.gif "0a286b0c-7f0d-46c5-9b56-29bef3a1deea")  
  
10. 在配置服务和终结点行为页上单击**下一步**。  
  
11. 在配置服务终结点绑定和地址页上**选择用于配置的协定**框中列出的 Siebel 业务组件为其选择选择操作页面上的操作的协定。 **下的所选的协定的操作**框显示所选的每个项目在选择操作页面上的操作。  
  
12. 在中**配置的地址和协定绑定**框中，指定以下设置的值：  
  
    |属性|指定的值|  
    |----------------------|-----------------------|  
    |绑定配置|该向导仅支持基本 HTTP 绑定。 因此，绑定配置字段自动填充到*System.ServiceModel.Configuration.BasicHttpBindingElement*。<br /><br /> 单击省略号按钮 **（...）** 来更改 HTTP 绑定的属性。 若要使用的安全通信通道，必须始终设置**模式下**属性设置为**传输**。 该向导设置的默认值为**模式下**属性作为**传输**。<br /><br /> 有关公开其他绑定的详细信息，请参阅[BasicHttpBindingElement 类](https://msdn.microsoft.com/library/system.servicemodel.configuration.basichttpbindingelement.aspx)。|  
    |端点名称|指定协定的终结点名称。|  
  
     此页上的其他字段已根据前面的页面中指定的值自动填充。  
  
     单击 **“应用”**。 执行此步骤中的下显示的所有协定**选择用于配置的协定**框。  
  
    > [!NOTE]
    >  如果不指定任何值在此页上，为所有协定接受默认值。  
  
     下图显示了配置服务终结点绑定和地址页上，使用指定的值。  
  
     ![配置服务终结点绑定和地址](../../adapters-and-accelerators/adapter-siebel/media/467d3e18-027d-4218-9d72-0740c1f559e3.gif "467d3e18-027d-4218-9d72-0740c1f559e3")  
  
13. 在配置服务终结点绑定和地址页上单击**下一步**。 摘要页列出了所选的 Siebel 业务组件以及下，为每个业务组件选择的操作协定的树状结构。  
  
14. 查看摘要，然后依次**完成**。  
  
15. 该向导创建 WCF 服务并添加到以下文件[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]项目：  
  
    1.  .svc 文件。 这是 WCF 服务文件。 向导将生成每个协定的一个文件。  
  
    2.  Web.config 文件。  
  
    3.  服务代码 （.cs 文件）。  
  
16. WCF 服务发布。  
  
    1.  请确保 Internet 信息服务 (IIS) 已启用 SSL。 请参阅[如何设置 SSL](https://docs.microsoft.com/iis/manage/configuring-security/how-to-set-up-ssl-on-iis)。
  
    2.  右键单击解决方案资源管理器中的项目，然后单击**发布**。  
  
    3.  在中**发布 Web**对话框框中，指定 WCF 服务的 URL。 例如：  
  
        ```  
        https://<computer_name>/Siebel_Account/  
        ```  
  
    4.  从**副本**框中，单击**所有项目文件**。  
  
    5.  单击“发布” 。  
  
17. 验证已成功发布 WCF 服务。  
  
    1.  启动 IIS Microsoft 管理控制台。 单击**启动**，依次指向**管理工具**，然后单击**Internet Information Services**。  
  
    2.  导航到发布服务的节点。 有关**Siebel_Account**服务，请导航到**Internet Information Services** > **\<计算机名称\>**  > **网站** > **默认网站** > **Siebel_Account**。  
  
    3.  在右窗格中，右键单击 BusinessObjects_Account_Account_Operation.svc 文件，然后单击**浏览**。  
  
    4.  Web 页会显示用于检索 WSDL 的 url。 您可能想要测试使用 svcutil 命令的元数据检索。 例如，若要检索 Siebel_Account 服务的元数据的命令是：  
  
        ```  
        svcutil.exe https://localhost/Siebel_Account/BusinessObjects_Account_Account_Operation.svc?wsdl  
        ```  
  
## <a name="next-steps"></a>后续步骤  
 现可用于 Siebel 业务组件的 WCF 服务。 使用 Business Data Catalog Definition Editor 创建 Siebel 业务组件操作的应用程序定义文件。 请参阅[步骤 2： 为 Siebel 业务组件操作创建应用程序定义文件](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md)有关的说明。 应用程序定义文件来确定存储 LOB 数据和在其中存储的格式。  
  
## <a name="see-also"></a>请参阅  
 [教程 1：在 SharePoint 站点上从 Siebel 系统提供数据](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)