---
title: 演练： 以编程方式执行策略 |Microsoft Docs
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6398e7af-2ed1-4596-879c-3b7d000b8de2
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 666b674e30e548489478af898d5fe88c47d21f14
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985718"
---
# <a name="walkthrough-executing-the-policy-programmatically"></a>演练： 以编程方式执行策略
本演练提供了分步过程调用中创建的策略[演练： 创建简单业务策略](../core/walkthrough-creating-a-simple-business-policy.md)演练从一个控制台应用程序以编程方式。  

## <a name="prerequisites"></a>必要條件  
 必须完成[演练： 创建简单业务策略](../core/walkthrough-creating-a-simple-business-policy.md)演练在执行本演练之前。  

## <a name="overview-of-this-walkthrough"></a>本演练概述  
 本概览包含两个过程，如下表所述。  

|过程标题|过程说明|  
|---------------------|---------------------------|  
|使用 Policy.Execute 方法调用 ProcessPurchaseOrder 策略|提供了通过使用调用策略的分步说明**Policy.Execute**方法。|  
|使用 RuleEngine.Execute 方法调用 ProcessPurchaseOrder 策略|提供了通过使用调用策略的分步说明**RuleEngine.Execute**方法。|  

### <a name="to-invoke-the-processpurchaseorder-policy-by-using-the-policyexecute-method"></a>使用 Policy.Execute 方法调用 ProcessPurchaseOrder 策略  

1. 启动**Microsoft Visual Studio**。  

2. 在中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，然后在**文件**菜单中，依次指向**新建**，然后单击**项目**。  

3. 在中**新的项目**对话框框中，执行以下操作：  


   |             使用此选项              |                             执行的操作                              |
   |-----------------------------------|---------------------------------------------------------------------|
   |         **项目类型**         |                        单击**Visual C#**。                         |
   |           **模板**           |                   单击**控制台应用程序**。                    |
   |             **名称**              |                       类型**ConsoleClient**。                       |
   |           **位置**            |     指定要保存项目文件的文件夹。      |
   |         **解决方案名称**         |                     类型**ConsoleClientSol**。                      |
   | **创建解决方案的目录** | 选中此复选框以便为解决方案文件创建目录。 |


4. 单击“确定” 。 **ConsoleClient**项目应该显示在解决方案资源管理器。 如果看不到解决方案资源管理器，请单击**解决方案资源管理器**上**视图**菜单。  

5. 在解决方案资源管理器中右键单击**引用**，然后单击**添加引用**。  

6. 单击**浏览**，浏览到**\Program Files\Common Files\Microsoft BizTalk**，然后双击**Microsoft.RuleEngine.dll**。  

7. 将以下行添加到顶部**Program.cs**之后的现有文件`using`语句：  

   ```  
   //To use the XmlDocument class  
   using System.Xml;  
   //To use the TypedXmlDocument and Policy classes  
   using Microsoft.RuleEngine;   
   ```  

8. 将以下代码添加到**Main**函数来创建**TypedXmlDocument**对象基于 XML 文档：  

   ```  
   XmlDocument doc = new XmlDocument();  
   //Loading the XML from SamplePO.xml file.  
   //Change the directory as needed  
   doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
   TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
   ```  

9. 将以下代码添加到**Main**函数以执行策略：  

    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  

10. 打印的值的输出 XML 以确认**状态**字段设置为**Approved**。 请注意，与不同的业务规则编辑器中，调用**Policy.Execute**方法不会更改原始文档。  

    ```  
    //Print the output document  
    Console.WriteLine(txd.Document.OuterXml);   
    ```  

11. 上**构建**菜单上，单击**生成 ConsoleClient**。  

12. 按 CTRL+F5 执行此应用程序。 确认的值**状态**字段设置为**Approved**。  

### <a name="to-invoke-the-processpurchaseorder-policy-by-using-the-ruleengineexecute-method"></a>使用 RuleEngine.Execute 方法调用 ProcessPurchaseOrder 策略  

1.  在解决方案资源管理器中右键单击**引用**，然后单击**添加引用**。  

2.  单击**浏览**，浏览到**\Program Files\Common Files\Microsoft BizTalk**，然后双击**Microsoft.BizTalk.RuleEngineExtensions.dll**。  

3.  注释掉以下行中**Program.cs**文件：  

    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  

4.  在注释掉的代码后面添加下列代码，以访问规则引擎数据库：  

    ```  
    //Get access to the SQL rule store   
    Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
    dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
    SqlRuleStore sqlRuleStore = (SqlRuleStore)dd.GetRuleStore();  
    ```  

5.  添加以下代码以访问**RuleSetInfoCollection** ProcessPurchaseOrder 策略：  

    ```  
    //Get access to RuleSetInfoCollection for the   
    //ProcessPurchaseOrder policy  
    RuleSetInfoCollection rsic = sqlRuleStore.GetRuleSets("ProcessPurchaseOrder", RuleStore.Filter.All);  
    ```  

6.  添加以下代码以创建**RuleSet**对象基于 ProcessPurchaseOrder 策略的规则集信息：  

    ```  
    //Create a RuleSet object based on the rule set information   
    //for the ProcessPurchaseOrder policy  
    RuleSet rs = sqlRuleStore.GetRuleSet(rsic[0]);  
    ```  

7.  添加以下代码以创建**RuleEngine**对象：  

    ```  
    //Create the RuleEngine object  
    Microsoft.RuleEngine.RuleEngine engine = new Microsoft.RuleEngine.RuleEngine(rs);  
    ```  

8.  添加以下代码以声明**TypedXmlDocument**到规则引擎工作内存的对象：  

    ```  
    //Assert the TypedXmlDocument object into working memory  
    //of the rule engine  
    engine.Assert(txd);  
    ```  

9. 现在，添加代码以使用执行策略**RuleEngine.Execute**方法：  

    ```  
    //Execute the policy by invoking RuleEngine.Execute method  
    engine.Execute();  
    ```  

10. 请确保**Console.WriteLine**语句是中的最后一个语句**Main**函数。  

11. 上**构建**菜单上，单击**生成 ConsoleClient**。  

12. 按 CTRL+F5 执行此应用程序。 确认的值**状态**字段设置为**Approved**。  

## <a name="comments"></a>注释  

-   完整代码**Main**函数通过使用执行 ProcessPurchaseOrder 策略**Policy.Execute**方法如下所示：  

    ```  
    static void Main(string[] args)  
    {  
    XmlDocument doc = new XmlDocument();  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    policy.Execute(txd);  
    Console.WriteLine(txd.Document.OuterXml);   
    }  
    ```  

-   使用执行 ProcessPurchaseOrder 策略的完整代码**RuleEngine.Execute**方法如下所示：  

    ```  
    static void Main(string[] args)  
    {  
    XmlDocument doc = new XmlDocument();  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
    dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
    SqlRuleStore sqlRuleStore = (SqlRuleStore)dd.GetRuleStore();  
    RuleSetInfoCollection rsic = sqlRuleStore.GetRuleSets("ProcessPurchaseOrder", RuleStore.Filter.All);  
    RuleSet rs = sqlRuleStore.GetRuleSet(rsic[0]);  
    Microsoft.RuleEngine.RuleEngine engine = new Microsoft.RuleEngine.RuleEngine(rs);  
    engine.Assert(txd);  
    engine.Execute();  
    Console.WriteLine(txd.Document.OuterXml);   
    }  
    ```  

-   您可能想要添加**console.readline （)** 末尾处的语句**Main**函数，以便应用程序等候你来终止该应用程序。  

-   在本演练中，客户端只向 ProcessPurchaseOrder 策略提交一个事实。 如果客户端需要提交到策略的多个事实，则需要创建一个事实数组并使用重载**Execute**将数组作为参数的方法。 下列示例代码演示了具体做法：  

    ```  
    Policy policy = new Policy("PolicyName");  
    object[] facts = new object[2];  
    facts[0] = txd;  
    facts[1] = new MyClass();  
    policy.Execute(facts);  
    policy.Dispose();  
    ```  

-   第一个参数**TypedXmlDocument**在代码中的构造函数是用来生成策略的类型的名称。  

-   **Policy.Execute**方法基本上是周围的包装**RuleEngine.Execute**方法。 因此，使用**Policy.Execute**如您所见本演练中，方法是调用某个策略的最简单的方法。  

-   更好地执行策略的控制，你可能想要使用**RuleEngine.Execute**而不是使用方法**Policy.Execute**。 例如，你可以暂时停止引擎通过使用**暂停**函数，并使用来然后恢复**Execute**函数。 有关详细信息，请参阅[暂停](../core/halt.md)。  

## <a name="see-also"></a>请参阅  
 [如何执行策略](../core/how-to-execute-policies.md)