---
title: 自定义 Functoid （BizTalk Server 示例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- functoids, customizing
- examples, functoids
- functoids, examples
- XML tools
- examples, XML tools
ms.assetid: 9f1eb260-ff62-46f5-a517-57f4e9172b35
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de71eb45faa6c5705cca2ef47061686608126577
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013381"
---
# <a name="custom-functoid-biztalk-server-sample"></a>自定义 Functoid （BizTalk Server 示例）
自定义 functoid 示例演示如何为 BizTalk 映射器编写自定义 functoid。 你可以向 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 工具箱添加此 functoid。 当 BizTalk 映射器获得焦点时，该 functoid 将显示在工具箱中。  
  
 自定义 functoid 应位于 BizTalk 映射器程序集中以便识别。 它可以使用任何一种符合 .NET 的语言进行编写，例如 C# 或 Visual Basic。  
  
 此外，自定义 functoid 必须派生自`Microsoft.BizTalk.BaseFunctoids`类，并必须通过重写它们提供对某些方法的实现。 (`BaseFunctoid`随附的 Microsoft.BizTalk.BaseFunctoids.dll 程序集中定义类[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。)  
  
## <a name="what-this-sample-does"></a>本示例的用途  
 自定义 Functoid 示例实现多个 functoid，每个派生自`BaseFunctoid`重写几个方法。  
  
 实现自定义 functoid 时，可以公开其内联代码。 内联代码负责为 functoid 执行计算。 BizTalk 映射器的编译器从 functoid 提取内联代码，并在生成项目时将其嵌入编译的 XSLT 中。  
  
 如果自定义 functoid 不公开任何内联代码，则 BizTalk 映射器将生成调用自定义 functoid 所在程序集的 XSLT。 在此情况下，必须确保自定义 functoid 程序集在全局程序集缓存中可用，以便 XSLT 引擎能够找到它。 自定义 functoid 还必须具有唯一的 GUID 属性。 BizTalk 映射器使用 GUID 标识要加载的程序集。  
  
> [!IMPORTANT]
>  如果你重用自定义 functoid 示例代码以实现自己的 functoid，则必须确保将 GUID 属性更改为唯一值。  
  
## <a name="where-to-find-this-sample"></a>本示例所在的位置  
 *\<示例路径\>* \XmlTools\CustomFunctoid  
  
 下表显示了本示例中的文件及其用途说明：  
  
|文件|Description|  
|---------------|-----------------|  
|AssemblyInfo.cs|程序集信息 C# 源代码。|  
|CBuildArray.bmp|工具箱位图。|  
|CConcat.bmp|工具箱位图。|  
|CExtractArray.bmp|工具箱位图。|  
|Cleanup.bat|用于取消部署程序集并从全局程序集缓存 (GAC) 删除这些程序集，同时删除 CustomFunctoid.dll。|  
|CLongestString.bmp|工具箱位图。|  
|CMultiply.bmp|工具箱位图。|  
|CustomFunctoid.cs|自定义 functoid C# 源代码。|  
|CustomFunctoid.csproj|自定义 functoid C# 项目。|  
|CustomFunctoid.sln|自定义 functoid 解决方案。|  
|CustomFunctoidResources.resx|自定义 functoid 资源。|  
|Setup.bat|用于生成、部署和启动示例。|  
  
## <a name="building-and-initializing-this-sample"></a>生成并初始化本示例  
 使用以下过程可以生成并初始化自定义 functoid 示例。  
  
#### <a name="to-build-and-initialize-this-sample"></a>构建和初始化此示例  
  
1.  在命令窗口中，将目录更改 (**cd**) 的以下文件夹：  
  
     \<*示例路径*\>\XmlTools\CustomFunctoid  
  
2.  运行 Setup.bat 文件，该文件将执行以下操作：  
  
    -   生成示例项目。  
  
    -   将生成的程序集复制到 Developer Tools\Mapper Extensions 目录中。  
  
    -   向 GAC 添加生成的程序集。  
  
        > [!NOTE]
        >  在尝试运行本示例前，你应确认在生成和初始化过程中未报告任何错误。  
  
## <a name="running-this-sample"></a>运行本示例  
 使用以下过程运行自定义 functoid 示例。  
  
#### <a name="to-run-this-sample"></a>运行本示例的步骤  
  
1. 从[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 项目中，单击**工具**菜单，然后选择**选择工具箱项**。  
  
2. 在中**选择工具箱项**对话框中，选择**BizTalk 映射器 Functoid**选项卡。  
  
3. 单击**重置**，然后单击**确定**。  
  
   > [!NOTE]
   >  如果自定义 functoid 没有公开任何内联代码，请确保 GAC 中包含其程序集。  
  
4. 从**文件**菜单中，选择**退出**以关闭[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
5. 启动**Visual Studio 命令提示符**。  
  
6. 在命令提示符处，键入**devenv /setup**。  
  
7. 启动**Microsoft Visual Studio**。  
  
    自定义 functoid （自定义 concatenate functoid、 最长字符串、 生成数组 functoid 和提取数组 functoid） 上显示**字符串 Functoid**工具箱和累计乘 functoid 的选项卡将显示在**累计 Functoid**选项卡。  
  
## <a name="removing-this-sample"></a>删除此示例  
 使用以下过程可以删除此自定义 functoid 示例。  
  
#### <a name="to-remove-this-sample"></a>删除本示例  
  
1. 从 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 工具箱中删除 functoid。  
  
   > [!WARNING]
   >  如果在运行 Cleanup.bat 后，仍在工具箱中看到过时的自定义 functoid（可能是由于 Visual Studio 内部缓存），请按照下面的步骤进行操作：  
  
   1. 从[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 项目中，单击**工具**菜单，然后选择**选择工具箱项**。  
  
   2. 在中**选择工具箱项**对话框中，选择**BizTalk 映射器 Functoid**选项卡。  
  
   3. 在列表中找到自定义 functoid（“自定义连接”functoid、“最长字符串”、“构建数组”functoid、“提取数组”functoid 和“累计乘”）。 单击各自**复选框**以删除 functoid，然后单击**确定**。  
  
      如果上述过程不起作用，则执行以下过程。  
  
   4. 从[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 项目中，单击**工具箱**时编辑映射以打开工具箱面板的选项卡。  
  
   5. 右键单击工具中，选择**选择项**。  
  
   6. 在选择项对话框中，单击**重置**，然后单击**确定**。  
  
   7. 关闭 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的所有实例。  
  
      如果上述过程不起作用，则执行以下过程。  
  
   8. 启动**Visual Studio 命令提示符**以管理员身份。  
  
   9. 关闭所有正在运行的 Visual Studio 的实例。  
  
   10. 发出以下命令：  
  
        `devenv /resetsettings`  
  
        `devenv /setup`  
  
   11. 可以从工具箱中手动选择不需要的 functoid。 然后，右键单击该 functoid，然后单击**删除**。  
  
       如果上述过程不起作用，则执行以下过程。  
  
   12. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk 项目中编辑映射时，单击“工具箱”选项卡打开工具箱面板。  
  
   13. 单击**累计 Functoid**组。  
  
   14. 右键单击你想要删除，然后选择的 functoid**删除**或按 delete 键。  
  
   15. 单击**字符串 Functoid**组。  
  
   16. 右键单击你想要删除，然后选择的 functoid**删除**或按 delete 键。  
  
2. 在命令窗口中，将目录更改 (**cd**) 的以下文件夹：  
  
    \<*示例路径*\>\XmlTools\CustomFunctoid  
  
3. 运行 Cleanup.bat 文件，该文件将执行以下操作：  
  
   -   从 Developer Tools\Mapper Extensions 目录中删除程序集。  
  
   -   从 GAC 删除程序集。  
  
## <a name="classes-or-methods-used-in-this-sample"></a>本示例中使用的类或方法  
 [Microsoft.BizTalk.BaseFunctoids.BaseFunctoid](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.basefunctoid.aspx)  
  
## <a name="see-also"></a>请参阅  
 [使用 BaseFunctoid](../core/using-basefunctoid.md)   
 [XML 工具（BizTalk Server 示例文件夹）](../core/xml-tools-biztalk-server-samples-folder.md)