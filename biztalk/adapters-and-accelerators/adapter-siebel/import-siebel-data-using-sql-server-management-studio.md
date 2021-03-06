---
title: 导入 Siebel 数据使用 SQL Server Management Studio |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio, importing data by using
- how to, import data by using SQL Server Management Studio
ms.assetid: 67da7f7b-37ea-4a31-89ef-a9f6974ff976
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdcc6140bb50ebca299cd58f78063be8f108dea4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013174"
---
# <a name="import-siebel-data-using-sql-server-management-studio"></a>导入 Siebel 数据使用 SQL Server Management Studio
本部分提供有关如何使用 SQL Server Management Studio 从 Siebel 系统到 SQL Server 数据库导入数据的信息。 它还说明了如何创建和执行 SSIS 包将此数据导入。  
  
## <a name="prerequisites"></a>必要條件  
 在执行之前在本主题中提供的过程，请确保：  
  
- [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]的计算机上安装。  
  
- 在计算机上安装 SQL Server Business Intelligence Development Studio。  
  
## <a name="importing-data-by-using-sql-server-management-studio"></a>使用 SQL Server Management Studio 导入数据  
 执行以下步骤将数据导入从 Siebel 系统使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]使用 SQL Server Management Studio。  
  
#### <a name="to-import-data-by-using-sql-server-management-studio"></a>若要使用 SQL Server Management Studio 导入数据  
  
1. 启动 SQL Server Management Studio。  
  
2. 在中**连接到服务器**对话框框中，指定的值以连接到 SQL Server 数据库，然后单击**Connect**。 Microsoft SQL Server Management Studio 将打开。  
  
3. 在对象资源管理器，展开 SQL Server 名称，展开**数据库**，并右键单击在其中你将会导出表从 Siebel 系统的数据库。 从上下文菜单中，指向**任务**，然后单击**导入数据**。 这将启动 SQL Server 导入和导出向导。  
  
4. 阅读欢迎屏幕上的信息，然后单击**下一步**。  
  
5. 在中**选择数据源**对话框中，从**数据源**下拉列表中，选择**Siebel eBusiness 应用程序的.NET Framework 数据提供程序**。 指定的不同的连接属性的值[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]连接字符串。 有关连接字符串属性的详细信息，请参阅[Siebel 连接字符串的数据提供程序属性](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md)。  
  
    单击“下一步” 。  
  
6. 在中**选择目标**对话框：  
  
   1.  从**目标**下拉列表中，选择**SQL Native Client**。  
  
   2.  从**服务器名称**下拉列表中，选择 SQL Server 名称。  
  
   3.  选择身份验证模式。  
  
   4.  从**数据库**下拉列表中，选择你想要导入 Siebel 表的数据库。  
  
   5.  单击“下一步” 。  
  
7. 在中**指定表复制或查询**对话框框中，选择**编写查询以指定要传输的数据**选项。  
  
8. 在中**提供源查询**对话框框中，指定用于筛选要导入到 SQL Server 的数据的选择查询。 有关语法的详细信息，为 SELECT 查询[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，请参阅[Siebel 中的选择语句的语法](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md)。  
  
    单击**分析**按钮以验证查询，单击**确定**在弹出对话框中，然后单击**下一步**。  
  
9. 在中**选择源表和视图**对话框框中，选择源和目标表对应的复选框。 源是指定从 Siebel 检索数据的查询。 目标是将在 SQL Server 数据库中创建的表。  
  
10. 该向导创建的源和目标之间的默认映射表字段。 但是，您可以根据需要更改映射。 若要更改字段映射，请单击**编辑映射**。  
  
     ![Siebel 和 SQL 表之间的列映射](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")  
  
11. 在中**列映射**对话框中，你可以：  
  
    -   更改目标表中的列的名称。  
  
    -   忽略某些列与目标表中。  
  
    -   更改目标表中的字段的数据类型。  
  
    -   更改其他字段属性，如可以为 null，大小、 精度和小数位数。  
  
         在完成后，单击 **“确定”**。  
  
12. 在中**选择源表和视图**对话框中，单击**下一步**。  
  
13. 在中**保存并执行包**对话框：  
  
    - 选择**立即执行**复选框，以执行查询。  
  
    - 选择**保存 SSIS 包**复选框以将查询另存为包和更高版本执行。 如果您选择保存包，您还必须指定想要将包保存在 SQL Server 或文件系统中。  
  
    - 从**包保护级别**下拉列表中，选择保护级别的包，并指定凭据所需的位置。  
  
    - 单击“下一步” 。  
  
      如果您选择保存包，请继续执行下一步。 否则，请跳到步骤 15。  
  
14. 在中**保存 SSIS 包**对话框框中，指定以下内容：  
  
    -   包的名称  
  
    -   包说明  
  
    -   如果您选择将包保存到 SQL Server，选择从一个 SQL Server**服务器名称**下拉列表。  
  
    -   如果您选择将包保存到文件系统中，指定的名称和位置中的文件**文件名**文本框。  
  
         在完成后，单击 **“下一步”**。  
  
15. 在中**完成该向导**对话框框中，查看操作，该向导将执行，然后单击摘要**完成**。  
  
16. 在中**正在执行操作**对话框中，该向导开始执行任务以从 Siebel 的信息导入到 SQL Server 数据库表中。 在向导中显示每个任务的状态。  
  
17. 已成功执行所有任务后，单击**关闭**。 如果任务失败时，请参阅相应的错误消息、 修复该问题，并重新运行该向导。  
  
## <a name="running-the-ssis-package"></a>运行 SSIS 包  
 如果您选择保存 SSIS 包，可以运行它来从 Siebel 系统中检索最新信息。 本部分提供有关如何运行包，如果您选择将其保存到文件系统信息。  
  
#### <a name="to-run-the-package-from-windows-explorer"></a>若要从 Windows 资源管理器中运行包  
  
1. 从**Windows 资源管理器**，导航到保存包的位置，然后双击包。  
  
2. 在“执行包实用工具”对话框中，单击“执行”。 **包的执行进度**对话框中显示不同的任务的进度。  
  
3. 已成功执行所有任务后，单击**关闭**。  
  
4. 在“执行包实用工具”对话框中，单击“关闭”。  
  
   有关正在运行的包的详细信息，请参阅"正在运行的包"网址[ http://go.microsoft.com/fwlink/?LinkId=94972 ](http://go.microsoft.com/fwlink/?LinkId=94972)。 有关任何 SSIS 包与相关的其他信息时，请参阅"包操作指南主题 (SSIS)" [ http://go.microsoft.com/fwlink/?LinkId=94973 ](http://go.microsoft.com/fwlink/?LinkId=94973)。  
  
## <a name="verifying-the-results"></a>验证结果  
 执行包之后, 必须通过转到 Siebel 数据导入到的 SQL Server 数据库来验证结果。 执行包应已创建表在目标数据库中。 应使用 Siebel 表中的值填充此表。  
  
## <a name="see-also"></a>请参阅  
 [使用 Siebel 的数据提供程序和 SSIS](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)