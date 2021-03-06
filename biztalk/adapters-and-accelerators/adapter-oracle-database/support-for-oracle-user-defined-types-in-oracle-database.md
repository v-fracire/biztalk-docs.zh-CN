---
title: 对 Oracle 数据库中的 Oracle 用户定义类型的支持 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 68edf0f2-a798-4096-86ca-85d2cfa9088a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bf839d214d0877ea51430cd0c4a7784ebfa3cc8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007054"
---
# <a name="support-for-oracle-user-defined-types-in-oracle-database"></a>对 Oracle 数据库中的 Oracle 用户定义类型的支持
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]包含 Oracle User-Defined 类型 (Udt) 的支持的 Oracle 数据库中执行对项目的操作。 Udt 可出现在以下项目：  
  
-   表和视图包含 UDT 列。  
  
-   包、 存储的过程和包含 UDT 参数的函数。  
  
## <a name="what-is-an-oracle-udt"></a>Oracle UDT 是什么？  
 Oracle Udt 帮助中的复杂实体表示为可以在应用程序之间共享的"单个"对象。 例如，就可以对模型实际实体，例如"客户"或"销售订单"为 Oracle 数据库中的对象。 在 Oracle 数据库中，定义 oracle Udt，它们的以下两种类型：  
  
- 对象类型。 例如，Oracle 对象。  
  
- 集合类型。 例如，嵌套的表类型或 VARRAY。  
  
  Oracle UDT 的名称是区分大小写，并且必须按以下方式指定: [SCHEMA_NAME]。[UDT_NAME]。  
  
## <a name="how-does-the-adapter-support-oracle-udt"></a>适配器如何支持 Oracle UDT？  
 ODP.NET 通过表示 Oracle 数据库中定义为.NET 类型 （自定义类型） 的 Oracle Udt 支持 Udt。 自定义类型到.NET 成员定义 Oracle UDT 属性或元素之间的映射。 自定义类型可以是.NET 类或结构，并可以表示 Oracle 对象或 Oracle 集合。  由于这一事实， [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ODP.NET 用于连接到 Oracle 数据库时，它将继承对 Oracle Udt 的支持。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 ODP.NET 来指定一个自定义类型映射，以将.NET 自定义类型映射到数据库中 Oracle UDT。 若要指定自定义类型映射，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用自定义类型工厂。 因此，若要使用 Oracle UDT，程序集 （.dll 文件） 是必需，用于定义自定义类型工厂。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ，可以生成自定义类型工厂生成的包含 Oracle UDT 项目/操作的元数据时的程序集。  
  
> [!NOTE]
>  适配器生成基于 ODP.NET 用于支持 Oracle Udt 类 Oracle Udt 的程序集。 有关如何在 ODP.NET 支持 Oracle Udt 的详细信息，请参阅[ http://go.microsoft.com/fwlink/?LinkId=140697 ](http://go.microsoft.com/fwlink/?LinkId=140697)。  
  
 若要生成在设计时使用 Oracle Udt 的程序集文件，然后它使用更高版本在运行时，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公开以下绑定属性：  
  
- **GeneratedUserTypesAssemblyFilePath** （设计时）  
  
- **GeneratedUserTypesAssemblyKeyFilePath** （设计时）  
  
- **UserAssembliesLoadPath** （运行时间）  
  
  有关这些绑定属性的信息，请参阅[用于 Oracle 数据库配置的绑定属性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
## <a name="performing-operations-on-artifacts-containing-oracle-udts"></a>对包含 Oracle Udt 的项目执行操作  
 若要在其中包含使用 Udt 的项目上执行操作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，必须执行以下操作在设计时和运行时。  
  
### <a name="design-time"></a>设计时  
 在 Visual Studio 中操作，必须执行以下步骤生成架构时。  
  
1. 连接到 Oracle 数据库使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，则[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 有关此操作的信息，请参阅[连接到 Oracle 数据库，在 Visual Studio 中使用使用适配器服务](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md)。  
  
2. 在连接时，在**绑定属性**选项卡**配置适配器**对话框框中，指定相应的值**GeneratedUserTypesAssemblyFilePath**并**GeneratedUserTypesAssemblyKeyFilePath**绑定属性。 有关这些绑定属性的信息，请参阅[用于 Oracle 数据库配置的绑定属性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
3. 当连接到 Oracle 数据库，在 Visual Studio 中时，浏览到包含 Oracle UDT 所需项目。 有关浏览项目的信息，请参阅[浏览、 搜索和获取 Oracle 数据库操作的元数据](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md)。  
  
4. 选择所需的项目，然后单击**确定**。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]生成所选的项目中的 Oracle UDT 程序集 （.dll 文件） 以及所选操作的元数据。 在中指定位置创建该程序集**GeneratedUserTypesAssemblyFilePath**属性绑定。  
  
5. 继续执行剩余的步骤用于生成和部署你的项目。  
  
### <a name="run-time"></a>运行时  
 在适配器客户端，若要对 Oracle Udt 执行操作，必须执行这些步骤。  
  
 **在 BizTalk Server 中**  
  
- 手动添加在步骤 4 中创建"设计时"到全局程序集缓存 (GAC) 在计算机上的 Oracle UDT 程序集。 或者，您可以手动复制 BizTalk Server 安装位置下的 Oracle UDT 程序集。 对于 BizTalk Server，这通常是\<安装驱动器\>: \Program Files\Microsoft BizTalk Server。  
  
- 配置时[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]WCF 自定义或 Wcf-oracledb 端口，在**绑定**选项卡上，指定 Oracle UDT 程序集的位置对于**UserAssembliesLoadPath**属性绑定。 有关此绑定属性的信息，请参阅[用于 Oracle 数据库配置的绑定属性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
  **在 Visual Studio 中**  
  
- 手动添加在步骤 4 中创建"设计时"到全局程序集缓存 (GAC) 在计算机上的 Oracle UDT 程序集。 或者，您可以手动将复制 Oracle UDT 程序集到项目可执行文件，这通常是在项目的 \bin\Debug 文件夹下与相同的位置。  
  
- 指定 Oracle UDT 程序集的位置**UserAssembliesLoadPath**属性绑定。 有关此绑定属性的信息，请参阅[用于 Oracle 数据库配置的绑定属性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
## <a name="see-also"></a>请参阅  
 [哪些操作可以是执行使用适配器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)