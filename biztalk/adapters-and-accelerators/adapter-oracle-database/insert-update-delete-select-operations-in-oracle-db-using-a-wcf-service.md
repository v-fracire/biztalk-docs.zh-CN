---
title: 插入、 更新、 删除或使用 WCF 服务模型的 Oracle 数据库中选择操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, Delete operation
- WCF service model, Select operation
- WCF service model, Insert operation
- WCF service model, Update operation
ms.assetid: d1a9f44f-ea0b-4dd6-9489-fa0d963848c4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91fa9b1828a8519dcbf7e1efba1db99ba84f1d0d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982446"
---
# <a name="insert-update-delete-or-select-operations-in-oracle-database-using-the-wcf-service-model"></a>插入、 更新、 删除或使用 WCF 服务模型的 Oracle 数据库中选择操作
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]显示一组基本的 Insert、 Update、 Delete 和 Oracle 数据库表和视图的 Select 操作。 通过使用这些操作，可以执行简单的 SQL INSERT、 UPDATE、 SELECT 和 DELETE 语句目标表或视图的 WHERE 子句的限定。 若要执行更复杂的操作，例如 SQL SELECT 查询使用联接运算符，可以使用 SQLEXECUTE 操作。 SQLEXECUTE 操作的详细信息，请参阅[WCF 服务模型中使用 Oracle 数据库执行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)。  
  
 下表总结了基本的 SQL 操作的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表和视图的图面。 有关这些操作的完整说明，请参阅[基本插入、 更新、 删除和选择表和视图操作的消息架构](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)。  
  
|运算|Description|  
|---------------|-----------------|  
|Insert|插入操作支持多个记录或大容量插入到目标表或视图：<br /><br /> -多个记录的插入操作将行插入到表或视图基于提供的记录集。<br />-如果在大容量插入操作将行插入到表或视图的基础提供 SQL SELECT 查询和列列表。 该查询将返回的记录插入到目标表基于列的列表。|  
|选择|对基于提供的列名称和一个筛选器字符串，指定 SQL WHERE 子句列表的目标表执行 SQL SELECT 查询。|  
|Update|在目标表上执行更新。 由一个筛选器字符串，指定 SQL WHERE 子句指定要更新的记录。 模板记录中指定的更新的值。|  
|DELETE|基于筛选器字符串中指定的 SQL WHERE 子句的目标表执行的删除。|  
  
## <a name="about-the-examples-used-in-this-topic"></a>有关使用在本主题中的示例  
 本主题中的示例使用 /SCOTT/ACCOUNTACTIVITY 表。 使用 SDK 示例提供了一个脚本来生成此表。 有关 SDK 示例的详细信息，请参阅[SDK 中的示例](../../core/samples-in-the-sdk.md)。  
  
## <a name="the-wcf-client-class"></a>WCF 客户端类  
 WCF 客户端生成的基本 SQL 操作的名称，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]图面基于表或视图，如以下表中所示的名称。  
  
|Oracle 数据库项目|WCF 客户端名称|  
|------------------------------|---------------------|  
|表|[架构]表 [TABLE_NAME] 客户端|  
|“查看”|[架构]视图 [VIEW_NAME] 客户端|  
  
 [架构] = Oracle 集合项目;例如，SCOTT。  
  
 [TABLE_NAME] = 表; 的名称例如，ACCOUNTACTIVITY。  
  
 [VIEW_NAME] = 视图的名称。  
  
 下表显示了对表的基本 SQL 操作的方法签名。 签名是相同的视图，只不过视图命名空间和名称替换这些表。  
  
|运算|方法签名|  
|---------------|----------------------|  
|Insert|长时间插入 ([TABLE_NS]。 [TABLE_NAME] RECORDINSERT [] 记录集，字符串 COLUMN_NAMES，查询字符串);|  
|选择|[TABLE_NS]。[TABLE_NAME]RECORDSELECT [] 选择 (string COLUMN_NAMES，字符串筛选器);|  
|Update|长时间更新 ([TABLE_NS]。 [TABLE_NAME] RECORDUPDATE 记录集，筛选器字符串）;|  
|DELETE|长时间删除 （字符串筛选器）;|  
  
 [TABLE_NS] = 表命名空间; 的名称例如，microsoft.lobservices.oracledb._2007._03.SCOTT。Table.ACCOUNTACTIVITY。  
  
 [TABLE_NAME] = 表; 的名称例如，ACCOUNTACTIVITY。  
  
 使用 Insert、 Update 和 Select 操作的记录类型都被定义为表中，或查看命名空间。  
  
 以下代码所示的 WCF 客户端类的方法签名为 Delete、 Insert、 Select 和 Update 生成/SCOTT/ACCOUNTACTIVITY 表的操作。  
  
```  
public partial class SCOTTTableACCOUNTACTIVITYClient : System.ServiceModel.ClientBase<SCOTTTableACCOUNTACTIVITY>, SCOTTTableACCOUNTACTIVITY {  
  
    public long Delete(string FILTER);  
  
    public long Insert(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[] RECORDSET, string COLUMN_NAMES, string QUERY);  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] Select(string COLUMN_NAMES, string FILTER);  
  
    public long Update(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE RECORDSET, string FILTER);  
}  
```  
  
## <a name="invoking-the-basic-sql-operations"></a>调用基本 SQL 操作  
 若要通过使用 WCF 客户端调用的基本 SQL 操作对表或视图，请执行以下步骤。  
  
1. 生成 WCF 客户端类为目标表或视图。 此类应包含将在目标项目调用操作方法。  
  
2. 创建 WCF 客户端类的实例并调用其方法来执行对表或视图的操作。  
  
   有关更多详细信息，有关如何创建 WCF 客户端类，并在调用操作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，请参阅[具有 Oracle 数据库适配器的 WCF 服务模型概述](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md)。  
  
   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] Oracle 数据库上执行一个事务内的每个操作。 可以通过设置控制此事务的隔离级别**TransactionIsolationLevel**属性绑定。 有关详细信息[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]绑定属性，请参阅[如何使用 BizTalk Adapter for Oracle 数据库绑定属性](https://msdn.microsoft.com/library/dd788467.aspx)。  
  
   以下部分提供有关如何调用在代码中的每个基本 SQL 操作的详细信息。  
  
###  <a name="BKMK_InsertOperation"></a> 插入操作  
 下表显示了如何设置多个记录插入的参数和大容量插入操作。  
  
|插入操作类型|记录集|COLUMN_NAMES|QUERY|  
|---------------------------|---------------|-------------------|-----------|  
|多个记录|应插入到目标的 INSERTRECORDS 的集合。|null|null|  
|大容量|null|以逗号分隔的目标; 中的列名称列表例如，"TID，帐户"。 列列表指定应在其中放置查询结果中每个插入的行的列。 查询必须返回匹配中数量和类型的列列表中指定的列的结果集。|对数据库表或视图返回的结果集将插入到目标; 的 SQL SELECT 查询例如，"选择 （TID，帐户） 从 NEW_TRANSACTIONS WHERE 帐户 = 100001"。 结果集必须与中数量和类型的列列表匹配。|  
  
 插入操作将返回记录插入到目标的数。  
  
> [!IMPORTANT]
>  在 WCF 服务模型中，插入操作中使用的记录集是强类型化。 可以设置为 nillable 列的值**null**记录要排除在执行插入操作; 在该列中但是，您不能设置为非 nillable 列的值**null**。 这意味着，在多个记录插入操作中，必须提供每个记录中的所有非 nillable 列的值。 此外，没有流式处理支持的基本 SQL 操作时使用 WCF 服务模型。 如果在多个记录的插入操作涉及大型记录集，这可能是一个重要考虑因素。 有关详细信息，请参阅[基本 SQL 操作调用使用 WCF 服务模型的限制](#BKMK_LimitationsInvoking)。  
  
 下面的代码演示以 ACCOUNTACTIVITY 表为目标的多个记录插入操作 （两条记录）。  
  
```  
// Insert records  
                using (SCOTTTableACCOUNTACTIVITYClient aaTableClient =   
                    new SCOTTTableACCOUNTACTIVITYClient("OracleDBBinding_SCOTT.Table.ACCOUNTACTIVITY"))  
                {  
                    long recsInserted;  
  
                    aaTableClient.ClientCredentials.UserName.UserName = "SCOTT";  
                    aaTableClient.ClientCredentials.UserName.Password = "TIGER";  
  
                    try  
                    {  
                        aaTableClient.Open();  
                    }  
                    catch (Exception ex)  
                    {  
                        // handle exception  
                        Console.WriteLine("Exception: " + ex.Message);  
                        throw;  
                    }  
  
                    // Do a multiple record Insert of 2 records for account 100001  
  
                    microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[] insertRecs =  
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[2];  
  
                                  TID__COMPLEX_TYPE tid = new TID__COMPLEX_TYPE();  
                                  tid.InlineValue = "tidSequence.NextVal()";  
  
                                  ACCOUNT__COMPLEX_TYPE account = new ACCOUNT__COMPLEX_TYPE();  
                                  account.Value = 100001;  
  
                    AMOUNT__COMPLEX_TYPE amount = new AMOUNT__COMPLEX_TYPE();  
                    amount.Value = 400;  
  
                    TRANSDATE__COMPLEX_TYPE transdate = new TRANSDATE__COMPLEX_TYPE();  
                    transdate.Value = DateTime.Now.Date;  
  
                    PROCESSED__COMPLEX_TYPE processed = new PROCESSED__COMPLEX_TYPE();  
                    processed.Value = "n";  
  
                    DESCRIPTION__COMPLEX_TYPE description1 = new DESCRIPTION__COMPLEX_TYPE();  
                    description1.Value = "Inserted Record #1";  
  
                    DESCRIPTION__COMPLEX_TYPE description2 = new DESCRIPTION__COMPLEX_TYPE();  
                    description2.Value = "Inserted Record #2";  
  
                    insertRecs[0] =   
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT();  
                    insertRecs[0].TID = tid;  
                    insertRecs[0].ACCOUNT = account;  
                    insertRecs[0].AMOUNT = amount;  
                    insertRecs[0].TRANSDATE = transdate;  
                    insertRecs[0].DESCRIPTION = description1;  
                    insertRecs[0].PROCESSED = processed;  
  
                    insertRecs[1] =   
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT();  
                    insertRecs[1].TID = tid;  
                    insertRecs[1].ACCOUNT = account;  
                    insertRecs[1].AMOUNT = amount;  
                    insertRecs[1].TRANSDATE = transdate;  
                    insertRecs[1].DESCRIPTION = description2;  
                    insertRecs[1].PROCESSED = processed;  
  
                    try  
                    {  
                        recsInserted = aaTableClient.Insert(insertRecs, null, null);  
                    }  
                    catch (Exception ex)  
                    {  
                        // handle exception  
                        Console.WriteLine("Exception: " + ex.Message);  
                        throw;  
                    }  
  
                    Console.WriteLine("Insert Done: {0} records inserted", recsInserted);  
```  
  
### <a name="select-operation"></a>选择操作  
 下表显示了用于选择操作的参数。  
  
|COLUMN_NAMES|FILTER|  
|-------------------|------------|  
|以逗号分隔的目标; 中的列名称列表例如，"TID，帐户"。 列列表中指定的目标应在结果集中返回的列。 未指定列列表中的列将设置为其返回的记录集的.NET 默认值。 对于 nillable 列，此值是**null**。|指定的查询; 目标行的 SQL WHERE 子句的内容例如，"DESCRIPTION = 插入记录 #1"。 可以将此参数设置为**null**返回目标的所有行。|  
  
 选择操作将返回基于目标的行类型的强类型的记录集。  
  
> [!IMPORTANT]
>  使用 WCF 服务模型时的基本 SQL 操作没有流式处理支持。 如果查询没有返回大型记录集，您可以通过使用 WCF 通道模型来提高性能。 有关详细信息，请参阅[基本 SQL 操作调用使用 WCF 服务模型的限制](#BKMK_LimitationsInvoking)。  
  
 下面的代码演示了面向 ACCOUNTACTIVITY 表选择操作。 返回的记录写入到控制台中。  
  
```  
// Declare a variable to hold the result set  
microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] selectRecords;  
  
// Select all records and write them to the console  
try  
{  
    selectRecords = aaTableClient.Select("*", null);  
}  
catch (Exception ex)  
{  
    // handle exception  
}  
  
Console.WriteLine("ACCOUNTACTIVITY before any operations");  
for (int i = 0; i \< selectRecords.Length; i++)  
{  
    Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", selectRecords[i].TID,  
    selectRecords[i].ACCOUNT,  
    selectRecords[i].AMOUNT,  
    selectRecords[i].TRANSDATE,  
    selectRecords[i].DESCRIPTION);  
}  
```  
  
> [!NOTE]
>  此代码省略了创建、 配置和打开 WCF 客户端实例的步骤。 有关示例，其中包括以下步骤，请参阅[插入操作](#BKMK_InsertOperation)。  
  
### <a name="update-operation"></a>更新操作  
 下表显示了更新操作的参数。  
  
|记录集|FILTER|  
|---------------|------------|  
|一个基于目标的行类型的强类型化的模板记录。 该模板记录指定目标行的更新的值。 对于 nillable 行的列，可以指定一个 null 值，以指示列不应更新目标行中。|在目标中指定要更新的行的 SQL WHERE 子句的内容。 例如，"DESCRIPTION = Inserted Record #1"。|  
  
 更新操作将返回从目标中删除的行数。  
  
> [!IMPORTANT]
>  在 WCF 服务模型中，更新操作中使用的模板记录是强类型化。 如果某一列为 nillable，则可以通过将其值设置为忽略更新操作中的列**null**中的模板记录; 但是，如果某列不为零，则必须设置模板记录中的其值。 例如，如果列是主键，它必须包含一个值。 有关详细信息，请参阅[基本 SQL 操作调用使用 WCF 服务模型的限制](#BKMK_LimitationsInvoking)。  
  
 下面的代码演示了面向 ACCOUNTACTIVITY 表的更新操作。  
  
```  
long recsUpdated;  
  
...  
  
// Create updated template. The TID, TIME, AMOUNT, and DESCRIPTION fields will be updated  
microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE updateRecord =  
    new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE();  
        updateRecord.TID = tidSequence.NextVal();  
        updateRecord.ACCOUNT = null;  
        updateRecord.AMOUNT = 300;  
        updateRecord.TRANSDATE = DateTime.Now.Date;  
        updateRecord.DESCRIPTION = "Updated Record #2";  
        updateRecord.PROCESSED = null;  
  
// Set filter string to specify the target record by using the DESCRIPTION field  
string filter = "DESCRIPTION = 'Inserted Record #2'";  
  
try  
{  
    recsUpdated = aaTableClient.Update(updateRecord, filter);  
}  
catch (Exception ex)  
{  
    // handle exception  
    ...  
}  
  
Console.WriteLine("{0} records updated", recsUpdated);  
```  
  
> [!NOTE]
>  此代码省略了创建、 配置和打开 WCF 客户端实例的步骤。 有关示例，其中包括以下步骤，请参阅[插入操作](#BKMK_InsertOperation)。  
  
### <a name="delete-operation"></a>删除操作  
 下表显示了删除操作的参数。  
  
|FILTER|  
|------------|  
|指定要从目标中删除的行的 SQL WHERE 子句的内容。 例如，"DESCRIPTION = Inserted Record #1"。|  
  
 删除操作将返回从目标中删除的行数。 下面的代码演示了面向 ACCOUNTACTIVITY 表删除操作。  
  
```  
// Set filter string equal to the DESCRIPTION field of the target record  
string filter = "DESCRIPTION = 'Inserted Record #1'";  
  
try  
{  
    recsDeleted = aaTableClient.Delete(filter);  
}  
catch (Exception ex)  
{  
    // handle exception  
  
    ...  
}  
Console.WriteLine("{0} records deleted", recsDeleted);  
```  
  
> [!NOTE]
>  此代码省略了创建、 配置和打开 WCF 客户端实例的步骤。 有关示例，其中包括以下步骤，请参阅[插入操作](#BKMK_InsertOperation)。  
  
##  <a name="BKMK_LimitationsInvoking"></a> 通过使用 WCF 服务模型中调用的基本 SQL 操作的限制  
 当使用 WCF 客户端调用的基本 SQL 操作时，存在以下限制：  
  
- **插入操作。** 多个记录的插入操作中使用的记录集是强类型化，因此包含的所有行的列。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]将解释为平均值的记录中的 null 值，应从插入操作中排除列; 但是，不为零的列，无法排除不能将其设置为 null 值。 因此，在执行多个记录的插入操作时必须指定不为零的列的值。  
  
- **插入操作。** [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]解释**DbNull** nillable 数据列来表示应从多个记录的插入操作中排除列中的值。 这意味着，您不能设置为 nillable 列**DbNull**的 Oracle 数据库中的多个记录插入操作。  
  
- **插入操作。** 涉及大型记录集的多个记录的插入操作没有流式处理支持。  
  
- **更新操作。** 在更新操作中使用的模板记录是强类型化，因此包含的所有行的列。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]解释来表示此记录中的 null 值，应从更新操作中排除列; 但是，不能因为为 null 值不能排除不为零的列。 因此，当执行更新操作时必须指定不为零的列的值。  
  
- **更新操作。** [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]解释**DbNull**模板记录来表示应从操作中排除列中的 nillable 数据列中的值。 这意味着，您不能设置为 nillable 列**DbNull**使用更新操作对 Oracle 数据库。  
  
- **选择操作。** 没有用于返回大型记录集的 SELECT 查询流式处理支持。  
  
  这些限制提出了挑战的情况下，你可以通过使用 WCF 通道模型，因为调用该操作：  
  
- 通过使用 WCF 通道模型，可以从更新和插入操作中排除特定的数据列。  
  
- WCF 通道模型提供节点级别流式处理支持基本的 SQL 操作的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公开。  
  
  有关使用 WCF 通道模型与详细信息[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，请参阅[开发 Oracle 数据库应用程序使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)。  
  
## <a name="see-also"></a>请参阅  
 [开发 Oracle 数据库应用程序使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)