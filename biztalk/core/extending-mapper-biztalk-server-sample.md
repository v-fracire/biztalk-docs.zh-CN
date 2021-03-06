---
title: 扩展映射器 （BizTalk Server 示例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Mapper, examples
- XML tools
- BizTalk Mapper, extending
- examples, BizTalk Mapper
- examples, XML tools
ms.assetid: 6010a13f-b715-4766-ad91-5aa9b98589e3
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff0cf33f00688b5b609123a644a5d2a298ecaf01
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995806"
---
# <a name="extending-mapper-biztalk-server-sample"></a>扩展映射器 （BizTalk Server 示例）
扩展映射器示例对如何使用和扩展 BizTalk 映射器进行演示。 本示例包含多个 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 映射文件 (.btm)，其中的每个文件均阐释了 BizTalk 映射器的一个功能。  

## <a name="what-this-sample-does"></a>本示例的用途  
 扩展映射器示例使用基于内容的路由 (CBR)，不使用业务流程。 通过在示例发送端口上指定筛选器，扩展映射器示例可直接连接到示例接收端口。 会在发送端口上指定一个要应用到已处理文档的映射。  

## <a name="where-to-find-this-sample"></a>本示例所在的位置  
 *\<示例路径\>* \XmlTools\ExtendingMapper  

 下表显示了本示例中的文件及其用途说明：  


|                                                                             文件                                                                             |                                                         Description                                                          |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| MapperClassLibrary\AssemblyInfo.cs、MapperClassLibrary\MapperClassLibrary.csproj、MapperClassLibrary\MapperHelper.cs 和 MapperClassLibrary\MapperClassLibrary.sln | Microsoft®[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]® 项目文件和 Visual C#® 源文件。 |
|                                                                           Cleanup.bat                                                                           |                      用于取消部署程序集并从全局程序集缓存 (GAC) 删除这些程序集。                       |
|                                                                         Destination.xsd                                                                         |                                                         架构文件。                                                         |
|                                                           ExtendingMapper.btproj、ExtendingMapper.sln                                                           |                                     本示例的 BizTalk 项目和解决方案文件。                                      |
|                                                                       ExtendingMapper.xml                                                                       |                                                         源 XML。                                                          |
|                                                                   ExtendingMapperBinding.xml                                                                    |                                                         绑定 XML。                                                         |
|                                                                      ExternalAssembly.xml                                                                       |                                                    外部程序集 XML。                                                    |
|                                                                      OverridingMapXslt.btm                                                                      |                                                          映射文件。                                                           |
|                                                                      OverridingMapXslt.xml                                                                      |                                                     替代映射 XML。                                                      |
|                                                                     OverridingMapXslt.xslt                                                                      |                                                 替代映射样式表。                                                  |
|                                                                Scriptor_CallExternalAssembly.btm                                                                |                                                       示例映射文件。                                                       |
|                                                            Scriptor_GlobalVariableInInlineScript.btm                                                            |                                                       示例映射文件。                                                       |
|                                                                   Scriptor_InlineScripts.btm                                                                    |                                                       示例映射文件。                                                       |
|                                                                     Scriptor_InlineXslt.btm                                                                     |                                                       示例映射文件。                                                       |
|                                                         Scriptor_InlineXsltCallingExternalAssembly.btm                                                          |                                                       示例映射文件。                                                       |
|                                                                  Scriptor_XsltCalltemplate.btm                                                                  |                                                       示例映射文件。                                                       |
|                                                                            Setup.bat                                                                            |                                           用于生成和初始化示例。                                           |
|                                                                           Source.xsd                                                                            |                                                         架构文件。                                                         |

## <a name="building-and-initializing-this-sample"></a>生成并初始化本示例  
 使用以下过程可以生成并初始化扩展映射器示例。  

#### <a name="to-build-and-initialize-this-sample"></a>构建和初始化此示例  

1. 在命令窗口中，将目录更改 (**cd**) 的以下文件夹：  

    *\<示例路径\>* \XmlTools\ExtendingMapper  

2. 运行 Setup.bat 文件，该文件将执行以下操作：  

   - 为本示例创建输入 (\In) 和输出 (\Out) 文件夹。  

   - 编译并部署该示例的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 项目。  

   - 创建并绑定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置、发送和接收端口。  

     如果要使用 Scriptor_CallExternalAssembly.btm 或 Scriptor_InlineXsltCallingExternalAssembly.btm 映射，请在 Visual Studio 中打开 ExtendingMapper.sln 并做以下修改（否则转到步骤 3）：  

   1. 在解决方案资源管理器中，打开 Scriptor_CallExternalAssembly.btm。  

   2. 在映射器网格上选择脚本 functoid。  

   3. 在属性网格中，选择**脚本**属性，并单击省略号 （...） 按钮以配置 functoid 脚本。  

   4. 在中**配置脚本 Functoid**对话框中，选择**脚本 Functoid 配置**，并指定以下内容：  


      |      将此项设置       |                           与此                            |
      |---------------------|--------------------------------------------------------------|
      |   **脚本类型**   |                      外部程序集                       |
      | **脚本程序集** | Microsoft.Samples.BizTalk.ExtendingMapper.MapperClassLibrary |
      |  **脚本类**   |    Microsoft.Samples.BizTalk.ExtendingMapper.MapperHelper    |
      |  **脚本方法**  |                           MyConcat                           |


   5. 从[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]**文件**菜单中，选择**保存**若要将更改保存到映射文件，然后关闭解决方案。  

3. 按任意键继续执行 Setup.bat。  

   > [!IMPORTANT]
   >  如果要使用 Scriptor_InlineXsltCallingExternalAssembly.btm，则必须编辑 ExternalAssembly.xml 文件。 BizTalk 使用 ExternalAssembly.xml 将映射器扩展对象已注册的命名空间映射到 .NET 程序集。 由于将按照完全限定的名称（包括其自动生成的公钥标记）对依赖程序集进行引用，因此必须更新此值。 如果不想使用 Scriptor_InlineXsltCallingExternalAssembly.btm，则不必完成 a 到 e 的全部步骤。  

4. 在 Windows 资源管理器，导航到\<Windows 文件夹\>\assembly\\。  

   1. 右键单击**Microsoft.Samples.BizTalk.ExtendingMapper.MapperClassLibrary** ，然后选择**属性**。  

   2. 复制公钥标记值。  

   3. 在文本编辑器中，打开*\<示例路径\>* \XML Tools\ExtendingMapper\ExternalAssembly.xml。  

   4. 选择<strong>AssemblyName="Microsoft.Samples.BizTalk.ExtendingMapper.MapperClassLibrary，版本 = 1.0.0.0，区域性 = 中性，PublicKeyToken = 68496d20c737d84b"</strong>属性，并替换**PublicKeyToken**公钥标记值的值中复制步骤 c。  

   5. 保存并关闭 ExternalAssembly.xml。  

   > [!NOTE]
   >  在尝试运行本示例前，你应确认在生成和初始化过程中未报告任何错误。  

#### <a name="to-configure-enlist-and-start-the-send-port"></a>配置、登记并启动发送端口  

1. 单击**启动**，选择**所有程序**，选择**Microsoft BizTalk Server**，然后选择**BizTalk Server 管理**。  

2. 在 BizTalk Server 管理控制台中，单击以展开**BizTalk Server 管理**，单击此项可展开**BizTalk 组 [\<servername\>:\<管理数据库\>]**，并单击以展开**应用程序**。  

3. 单击此项可展开**ExtendingMapperApplication**，然后单击**发送端口**。  

4. 在右窗格中，右键单击**发送端口**，然后单击**属性**。  

5. 在中**ExtendingMapperSP – 发送端口属性**对话框中，单击**出站映射**页。  

    在中**地图**列中，从下拉列表中，选择所需的映射，然后单击**确定**。 下表对这些映射进行了说明。  


   |                                 “要应用的映射”属性                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   |---------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |       Microsoft.Samples.BizTalk.ExtendingMapper。 Scriptor_CallExternalAssembly        |                                                                                                                                                                                                                                                                                                                                       演示如何调用外部.NET 程序集从中的函数**脚本**functoid 在映射中，基于此 functoid 的输入参数。 这样做有助于将任何处理逻辑与映射文件完全分离。 此映射文件使用本示例附带的 MapperClassLibrary.dll 程序集。                                                                                                                                                                                                                                                                                                                                       |
   |           Microsoft.Samples.BizTalk.ExtendingMapper。 Scriptor_InlineScripts           |                                                                                                                                                                                                                                                                                                                                                                                                                 演示如何编写简单的内联脚本内**脚本**functoid 使用.NET 语言如 C#、 Visual Basic.NET 和 JScript.NET 的映射文件中。                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |   Microsoft.Samples.BizTalk.ExtendingMapper。 Scriptor_GlobalVariableInInlineScript    |                                                                                                                                                                                                                                                                                                                                                                                        演示如何在的内联脚本中使用全局变量**脚本**functoid。 全局变量通常用于维护跨不同的映射文件中的状态信息**脚本**functoid。                                                                                                                                                                                                                                                                                                                                                                                         |
   |            Microsoft.Samples.BizTalk.ExtendingMapper。 Scriptor_InlineXslt             |                                                                                                                                                                                                                                                                                                                                   演示如何构造使用原始内联 XSLT 在目标文档中的结构内**脚本**映射中的 functoid。 您可以构造目标文档中使用的某些部分**脚本**具有内联 XSLT 时不能为此，在 BizTalk 映射器中使用其他 functoid 的 functoid。                                                                                                                                                                                                                                                                                                                                   |
   |         Microsoft.Samples.BizTalk.ExtendingMapper。 Scriptor_XsltCalltemplate          |                                                                                                                                                                                                                                演示如何使用 XSLT 调用模板内的目标文档中创建结构**脚本**映射中的 functoid。 XSLT 是调用模板可以接受参数，因此您可以创建结构的内联 XSLT 调用模板的优于基于输入参数**脚本**functoid。 您可以构造目标文档中使用的某些部分**脚本**具有内联 XSLT 时不能为此，在 BizTalk 映射器中使用其他 functoid 的 functoid。                                                                                                                                                                                                                                 |
   | Microsoft.Samples.BizTalk.ExtendingMapper。 Scriptor_InlineXsltCallingExternalAssembly |                                                                                                                                                                                                                           演示如何调用外部.NET 程序集从的内联 XSLT 内的**脚本**functoid 在映射中的。 介绍了如何覆盖**自定义扩展 XML**与自定义扩展插件文件包含要调用的外部.NET 程序集的详细信息的 externalassembly_extxml.xml 取代 BizTalk 映射器网格的属性。 您可以构造目标文档中使用的某些部分**脚本**具有内联 XSLT 时不能执行该操作使用其他 functoid 在映射器 UI 中的 functoid。                                                                                                                                                                                                                           |
   |             Microsoft.Samples.BizTalk.ExtendingMapper。 OverridingMapXslt              | 演示如何使用自定义 XSLT 文件完全替代 BizTalk 映射器文件的已编译 XSLT。 您可以执行此操作通过重写**自定义 XSL 路径**属性和可选**自定义扩展 XML** BizTalk 映射器网格的属性。 你提供的自定义 XSLT 文件包含在要在运行时使用的项目的已编译 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 程序集中。 在这种情况下将忽略映射文件 (.btm) 的内容。 此映射文件使用 OverridingMapXslt.xslt 和 OverridingMapXslt.xml**自定义 XSL 路径**并**自定义扩展 XML**属性，分别。<br /><br /> 你可在解决方案资源管理器中对映射文件进行验证。 然后可以为您可以编辑和使用的模板文件将其**自定义 XSL 路径**BizTalk 映射器网格的属性。 一旦无法使用 BizTalk 映射器生成 XSLT，你即可使用此选项。 |

## <a name="running-this-sample"></a>运行本示例  
 使用以下过程运行扩展映射器示例。  

#### <a name="to-run-this-sample"></a>运行本示例的步骤  

1.  复制到输入文件夹中，输入文件 ExtendingMapper.xml *\<示例路径\>* \XmlTools\ExtendingMapper\In。  

2.  请注意，该文件将转换并路由到如何*\<示例路径\>* \XmlTools\ExtendingMapper\Out 文件夹。 发生的转换由应用的映射确定。  

## <a name="see-also"></a>请参阅  
 [XML 工具（BizTalk Server 示例文件夹）](../core/xml-tools-biztalk-server-samples-folder.md)