---
title: 如何设置警报 |Microsoft 文档
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- alerts, creating
- Query Builder [BAM portal], creating alerts
- queries [BAM], aggregations
- Query Builder [BAM portal], activity searches
- Query Builder [BAM portal], aggregation alerts
- queries [BAM], alerts
- aggregations, alerts
ms.assetid: 8745d2c6-5bc0-4d7a-8c17-361535f5c6e6
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 774fbab86c1da1389b813f621c89f38cf0aa7656
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255701"
---
# <a name="how-to-set-an-alert"></a>如何设置警报
通过将警报附加到活动搜索或钻取聚合，可设置警报。  
  
> [!NOTE]
>  在设置查询警报之前，应先运行该查询，评估警报周期持续时间是否适合您要监视的流程。 如果周期持续时间太短，则警报条件可能只是瞬时存在，因此可能被警报系统遗漏。  
  
> [!NOTE]
>  如果在这些过程中单击后退按钮，你可能会收到以下消息:"警告： 页面已过期。" 若要返回至以前的内容，请按 F5。 （可能需要多次按 F5。）  
  
> [!NOTE]
>  在视图上创建第一个警报时，将不会显示用于该警报的数据。 在定义警报阶段而并未实际创建警报之前，并不会收集该时间帧的警报数据。  
  
## <a name="prerequisites"></a>先决条件  
 以下为执行本主题中步骤的前提条件：  
  
-   必须具有已部署的视图。  
  
-   必须具有用于实例警报的活动搜索。  
  
-   必须具有用于聚合警报的已填充的聚合。  
  
### <a name="to-set-an-alert-on-an-activity-search"></a>设置有关活动搜索的警报  
  
1.  在**我视图**框架中，单击要展开的视图的任务列表中的视图。  
  
2.  单击**活动搜索**你展开视图下的任务。  
  
3.  创建或打开活动搜索。 有关如何执行此操作的信息，请参阅[How to Create in 活动搜索查询](../core/how-to-create-a-query-in-activity-search.md)。  
  
4.  在 BAM 门户的内容框架中，单击**设置警报**按钮。 该内容框架中将加载警报创建模板。  
  
5.  在**名称**文本框中，键入警报的描述性名称。  
  
    > [!NOTE]
    >  名称限制为 100 个字符并且不能包含以下字符: ~ ！ @# $%^&amp;* （); 如果在名称中输入以下任意字符，虚线的红色边框的边框，该值指示错误。 请纠正以完成操作的文本字段。  
  
6.  如果您不希望在此时间启用的警报，清除**警报启用**复选框。  
  
7.  在**消息**文本框中，键入时，将触发警报传递的消息。  
  
8.  从**优先级**下拉列表中，选择此警报的优先级。 优先级设置表示设置警报的问题的严重性。  
  
9. 在**所有者**文本框中，键入此警报的所有者的别名。 在多个用户名之间使用分号将其隔开。  
  
10. 在**警报安全**区域中，选择此复选框以允许其他用户看到此警报并订阅它。  
  
    > [!NOTE]
    >  可以随时在私有和公共之间切换警报安全性，即使该警报有订户，也可以进行切换。 但是，在将警报安全性从公共切换为私有时，应该考虑该警报是否有订户。 如果该警报有订户，在警报切换为私有后，他们将无法编辑订阅的警报。  
  
11. 在右上角的**警报详细信息**区域中，单击**保存警报**按钮。  
  
### <a name="to-set-an-alert-on-an-aggregation"></a>设置有关聚合的警报  
  
1.  在**我视图**框架中，单击要展开的视图的任务列表中的视图。  
  
2.  单击**聚合**任务中**我视图**下展开的视图。  
  
3.  在 BAM 门户的内容框架中，右键单击数据透视表总计列中的单元格。 这时将打开上下文菜单，其中包含可用于执行聚合总计的函数。  
  
    > [!NOTE]
    >  通过展开行项目，可以对聚合总计的特定组件设置警报。 您可以以此方式展开随后的级别，直到到达要设置警报的级别。  
  
4.  在上下文菜单的顶部，单击**创建警报**。 该内容框架中将加载警报创建模板。  
  
5.  在**名称**文本框中，键入警报的描述性名称。  
  
    > [!NOTE]
    >  名称限制为 100 个字符并且不能包含以下字符: ~ ！ @# $%^&amp;* （); 如果在名称中输入以下任意字符，虚线的红色边框的边框，该值指示错误。 请纠正以完成操作的文本字段。  
  
6.  如果您不希望在此时间启用的警报，清除**警报启用**复选框。  
  
7.  在**消息**文本框中，键入时，将触发警报传递的消息。  
  
8.  从**优先级**下拉列表中，选择此警报的优先级。 优先级设置表示设置警报的问题的严重性。  
  
9. 在**所有者**文本框中，键入此警报的所有者的别名。 在多个用户名之间使用分号将其隔开。  
  
10. 在**阈值**区域中，选择比较条件从**计数**下拉列表。  
  
11. 在**持续时间**文本框中，输入在其阈值的测量的时间单位数。  
  
12. 从**持续时间**下拉列表中，选择的时间单位。  
  
13. 在**警报安全**区域中，选择此复选框以允许其他用户看到此警报并订阅它。  
  
    > [!NOTE]
    >  可以随时在私有和公共之间切换警报安全性，即使该警报有订户，也可以进行切换。 但是，在将警报安全性从公共切换为私有时，应该考虑该警报是否有订户。 如果该警报有订户，在警报切换为私有后，他们将无法编辑订阅的警报。  
  
14. 在右上角的**警报详细信息**区域中，单击**保存警报**按钮。  
  
## <a name="see-also"></a>另请参阅  
 [如何创建活动搜索查询](../core/how-to-create-a-query-in-activity-search.md)