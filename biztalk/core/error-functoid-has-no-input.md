---
title: 错误-Functoid 具有任何输入 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.functiodHasNoInput
ms.assetid: ea59b902-953d-4a5f-aa28-dbaa0a017dca
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fd2626d0b3332ddbf2def47502e7b323a0ae0e7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000774"
---
# <a name="error---functoid-has-no-input"></a>错误-Functoid 具有任何输入
**错误代码**  

 btm1012  

 **说明**  

 所指示的 functoid 至少需要一个输入参数，但当前未指定任何输入参数。  

 **用户执行任何操作**  

 采用以下一种或两种方法为所指示的 functoid 提供适当数目的输入参数，特别要注意输入参数的正确顺序：  

- 拖动鼠标，在所指示的 functoid 与源架构中的节点或其他 functoid 的输出之间创建链接，这些 functoid 在映射网格页中位于所指示的 functoid 的左侧。  

- 选择所指示的 functoid，单击省略号 (**...**) 按钮与相关联**输入参数**属性在 microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]属性窗口中，然后配置并重新排列输入参数的顺序**配置\<Functoid\> Functoid**对话框。 也可以创建常数输入参数并为它赋值，然后在此对话框中将该参数放置到相对于其他输入参数的正确位置。
