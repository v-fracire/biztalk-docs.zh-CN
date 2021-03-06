---
title: 从另一个策略调用某个策略 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5bf658a-02a1-426a-abe5-8c9de673cf0d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39f1366ccbf199db02bc60c0caf9015aba0cfc03
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994030"
---
# <a name="invoking-a-policy-from-another-policy"></a>从其他策略调用策略
您可以通过使用以下方式之一从其他策略（父策略）调用策略（子策略）：  
  
- 调用**Policy.Execute**方法直接从父策略  
  
- 调用帮助程序.NET 组件的方法包装**Policy.Execute**从父策略的方法  
  
  使用第二种方法的优点是，您可以添加预处理和后处理代码**Policy.Execute**方法。 例如，您可以在此包装程序方法中创建子策略所需的任何事实。 下面几部分将为每个方法提供一个示例。  
  
## <a name="invoking-the-policyexecute-method-directly-from-the-parent-policy"></a>直接从父策略调用 Policy.Execute 方法  
 本部分介绍通过使用调用子策略从父策略的高级步骤**Policy.Execute**直接方法。  
  
### <a name="adding-the-policyexecute-action-to-the-parent-policy"></a>向父策略添加 Policy.Execute 操作  
 以下过程包含添加的步骤**Policy.Execute**方法作为操作保存到父策略，将 XML 文档作为事实传递到子策略。  
  
##### <a name="to-add-the-policyexecute-method-as-an-action-to-a-policy"></a>将 Policy.Execute 方法作为操作添加到某一策略  
  
1.  在事实浏览器窗口中，单击 **.NET 类**选项卡。  
  
2.  右键单击 **.NET 程序集**，然后单击**浏览**。  
  
3.  选择**Microsoft.RuleEngine**从 **.NET 程序集**列表，，然后单击**确定**。  
  
4.  展开**策略**。  
  
5.  拖动**Execute (Object facts)** 或**Execute （Object facts，IRuleSetTrackingInterceptor trackingInterceptor）** 到那么窗格。  
  
6.  单击**XML 架构**节点。  
  
    > [!NOTE]
    >  在此示例方案中，将作为事实提交到父策略的 XML 文档作为事实传递到子策略。 您可以调用为子策略创建事实的 .NET 方法。  
  
7.  右键单击**架构**，然后单击**浏览**。  
  
8.  选择你想要将作为事实传递，然后单击 XML 文档的架构**打开**。  
  
9. 拖动*\<架构名称\>* 的第一个参数为.xsd **Policy.Execute**方法将传递到子策略事实作为传递到父策略的 XML 文档。  
  
10. 如果您使用**Execute**方法不采用**IRuleSetTrackingInterceptor**作为第二个参数，请跳过以下步骤。  
  
11. 单击 **.NET 类**选项卡。  
  
12. 拖动**DebugTrackingInterceptor**中**Microsoft.RuleEngine**到的第二个参数**Policy.Execute**方法。  
  
    > [!NOTE]
    >  如果你执行此操作，客户端必须传递的实例**DebugTrackingInterceptor**类作为事实到父策略，再将该实例作为事实传递到子策略。 您可以拖动的构造函数**DebugTrackingInterceptor**类，以便为你自动创建该实例。  
  
### <a name="modifying-the-client-application-that-invokes-the-parent-policy"></a>修改调用父策略的客户端应用程序  
 调用父策略的客户端创建的实例**策略**类子策略名称作为参数并将其作为事实传递到父策略与其他事实一起。 下列示例代码阐释了这一操作：  
  
```  
DebugTrackingInterceptor dti = new DebugTrackingInterceptor("PolicyTracking.txt");  
Policy policy = new Policy("ParentPolicy");  
object[] facts = new object[3];  
facts[0] = txd;  
facts[1] = new Policy("ChildPolicy");  
facts[2] = new DebugTrackingInterceptor("PolicyTracking2.txt");  
policy.Execute(facts, dti);  
policy.Dispose();  
```  
  
 如果客户端是 BizTalk 业务流程，可能需要放置代码以创建事实**表达式**形状，然后事实作为参数传递给**调用规则**形状。  
  
## <a name="invoking-a-net-wrapper-method-from-the-parent-policy"></a>从父策略调用 .NET 包装程序方法  
 本部分介绍调用包装到调用的.NET 方法的概要步骤**Policy.Execute**从父策略的方法。  
  
### <a name="creating-the-utility-net-class"></a>创建实用程序 .NET 类  
  
##### <a name="to-create-the-utility-class"></a>创建实用程序类  
  
1.  创建一个 .NET 类库项目，然后向该项目添加某一类。  
  
2.  调用的静态方法添加**Policy.Execute**方法调用策略的名称作为参数进行传递，如下面的示例代码中所示：  
  
    ```  
    public static void Execute(string policyName, TypedXmlDocument txd)  
    {  
        DebugTrackingInterceptor dti = new   DebugTrackingInterceptor("PolicyTracking.txt");  
        Policy policy = new Policy("ParentPolicy");  
        object[] facts = new object[3];  
        facts[0] = txd;  
        facts[1] = new Policy("ChildPolicy");  
        facts[2] = new DebugTrackingInterceptor("PolicyTracking2.txt");  
        policy.Execute(facts, dti);  
        policy.Dispose();  
    }   
    ```  
  
3.  请确保**StaticSupport**注册表项设置为 1 或 2。 有关该注册表项的详细信息，请参阅[类的调用静态成员](../core/invoking-static-members-of-a-class.md)。  
  
    > [!NOTE]
    >  您可以使用某一实例方法来代替静态方法。 请记住，如果您使用某一实例方法，则客户端必须将帮助程序 .NET 类的实例作为事实传递到父策略。  
  
### <a name="modifying-the-client-application"></a>修改客户端应用程序  
 客户端调用父策略，并且父策略所调用的帮助程序方法将调用子策略。 该客户端的示例代码如下：  
  
```  
facts[0] = txd;  
facts[1] = new PolicyExecutor(txd);  
//call the first or parent policy  
Policy policy = new Policy(policyName);  
DebugTrackingInterceptor dti = new DebugTrackingInterceptor("PolicyTracking.txt");  
policy.Execute(facts, dti);  
policy.Dispose();  
```  
  
> [!NOTE]
>  如果该方法是一个实例方法，则客户端必须创建帮助程序 .NET 类的一个实例，并且将该实例作为事实传递到父策略。  
  
> [!NOTE]
>  如果客户端是 BizTalk 业务流程，可能需要放置代码以创建事实**表达式**形状，然后事实作为参数传递给**调用规则**形状。