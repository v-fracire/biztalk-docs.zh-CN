---
title: 步骤 2： 创建公用和私用证书 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating certificates
- public certificates
- certificates, public certificates
- creating, certificates
- private certificates
ms.assetid: 0a925d89-03d9-41fe-907b-85a6ae42362a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f31d1bb1dcc5a0e6f587797f41e97d16ca6606da
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007606"
---
# <a name="step-2-creating-public-and-private-certificates"></a>步骤 2： 创建公用和私用证书
在此步骤中，使用证书颁发机构中创建[步骤 1： 创建证书颁发机构&#91;RN3&#93; ](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)以生成 Contoso 和 Fabrikam 组织使用的公钥和私钥证书。  

### <a name="to-generate-the-contoso-and-fabrikam-encryption-certificates"></a>生成 Contoso 和 Fabrikam 加密证书  

1. 在用作证书颁发机构的计算机上，在 Internet Explorer 中找到并打开 http://<contoso 计算机名称>/certsrv。  

2. 上**欢迎**页上，单击**申请一个证书**。  

3. 上**申请一个证书**页上，单击**高级的证书申请**。  

4. 上**高级证书申请**页上，单击**创建并向此 CA 提交一个申请**。  

5. 上**高级证书申请**页上，执行以下操作：  


   |            使用此选项            |                                                                         执行的操作                                                                         |
   |--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |            **名称**            |                                                               类型**Fabrikam 加密**。                                                                |
   |           **电子邮件**           |                                                          类型<strong>jdoe@fabrikam.com</strong>。                                                          |
   |          **Company**           |                                                                     类型**Fabrikam**。                                                                     |
   |         **部门**         |                                                                       类型**测试**。                                                                       |
   |            **City**            |                                                                       类型**测试**。                                                                       |
   |           **State**            |                                                                       类型**测试**。                                                                       |
   |       **国家/地区**       |                                                                        类型**美国**。                                                                        |
   | **需要的证书类型** |                                             选择**电子邮件保护证书**从下拉列表。                                              |
   |         **密钥用法**          |                                                              选择**Exchange**选项。                                                               |
   |   **附加密钥选项**   | 请选中以下选项：<br /><br /> -   **标记密钥为可导出**<br />-   **将证书保存在本地计算机证书存储** |
   |       **友好名称**        |                                                               类型**Fabrikam 加密**。                                                                |


6. 单击**提交**，然后单击**是**中**Web 访问确认**对话框。  

7. 上**证书颁发**页上，单击**安装此证书**。  

8. 重复步骤 1-7，更改中的信息**名称**框中**识别信息**部分并**好记的名称**框**Contoso加密**。  

### <a name="to-generate-the-contoso-and-fabrikam-signing-certificates"></a>生成 Contoso 和 Fabrikam 签名证书  

1. 在 Internet Explorer 中，找到并打开 http://<contoso 计算机名称>/certsrv。  

2. 上**欢迎**页上，单击**申请一个证书**。  

3. 上**申请一个证书**页上，单击**高级的证书申请**。  

4. 上**高级证书申请**页上，单击**创建并向此 CA 提交一个申请**。  

5. 上**高级证书申请**页上，执行以下操作：  


   |            使用此选项            |                                                                         执行的操作                                                                         |
   |--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |            **名称**            |                                                                类型**Fabrikam 签名**。                                                                |
   |           **电子邮件**           |                                                          类型<strong>jdoe@fabrikam.com</strong>。                                                          |
   |          **Company**           |                                                                     类型**Fabrikam**。                                                                     |
   |         **部门**         |                                                                       类型**测试**。                                                                       |
   |            **City**            |                                                                       类型**测试**。                                                                       |
   |           **State**            |                                                                       类型**测试**。                                                                       |
   |       **国家/地区**       |                                                                        类型**美国**。                                                                        |
   | **需要的证书类型** |                                             选择**电子邮件保护证书**从此下拉列表中。                                              |
   |         **密钥用法**          |                                                              选择**签名**选项。                                                              |
   |   **附加密钥选项**   | 请选中以下选项：<br /><br /> -   **标记密钥为可导出**<br />-   **将证书保存在本地计算机证书存储** |
   |       **友好名称**        |                                                                类型**Fabrikam 签名**。                                                                |


6. 单击**提交**，然后单击**是**要求申请证书时。  

7. 上**证书颁发**页上，单击**安装此证书**。  

8. 重复步骤 1-7，更改中的信息**名称**框中**识别信息**部分并**好记的名称**框**Contoso签名**。  

### <a name="to-generate-private-certificates-for-the-encryption-and-signature-certificates"></a>生成用作加密证书和签名证书的私用证书  

1.  单击**启动**，单击**运行**，类型**MMC**，然后单击**确定**。  

2.  在 console1 窗口中，在**文件**菜单上，单击**添加/删除管理单元中**。  

3.  在添加/删除管理单元对话框中，在**独立**选项卡上，单击**添加**。  

4.  在添加独立管理单元对话框中，选择**证书**中管理单元**可用的独立管理单元**列表，，然后单击**添加**。  

5.  在证书管理单元对话框中，选择**我的用户帐户**，然后单击**下一步**。  

6.  在选择计算机对话框中，单击**完成**。  

7.  在添加独立管理单元对话框中，单击**关闭**。  

8.  在添加/删除管理单元对话框中，单击**确定**。  

9. 在 console1 窗口中，展开**证书 （本地计算机）**，展开**个人**，然后单击**证书**。  

10. 在右窗格中，右键单击**Fabrikam 加密**证书，依次指向**的所有任务**，然后单击**导出**。  

11. 上**欢迎使用证书导出向导**页上，单击**下一步**。  

12. 上**导出私钥**页上，选择**是，导出私钥**，然后单击**下一步**。  

13. 上**导出文件格式**页上，请确保**个人信息交换**是唯一的选项选择，然后依次**下一步**。  

14. 上**密码**页上，在**密码**并**确认密码**框中，键入**mysecret**，然后单击**下一步**.  

15. 上**文件导出**页上，单击**浏览**。  

16. 在中**另存为**对话框中，将证书使用的文件路径保存*\<驱动器\>*: \Certs\Fabrikam Private Encryption.pfx。  

17. 上**导出的文件**页上，单击**下一步**。  

18. 上**正在完成证书导出向导**页上，单击**完成**。  

19. 在指示导出成功证书导出向导弹出窗口中，单击**确定**。  

20. 对于“Fabrikam 签名”证书，请重复步骤 10 到步骤 19，并使用 Fabrikam Private Signature.pfx 文件名。  

21. 对于“Contoso 签名”证书和“Contoso 加密”证书，请分别重复步骤 10 到步骤 19，并分别使用 Contoso Private Signature.pfx 和 Contoso Private Encryption.pfx 文件名。  

### <a name="to-generate-public-certificates-for-the-encryption-and-signature-certificates"></a>生成用作加密证书和签名证书的公用证书  

1.  在 console1 窗口中，展开**证书-当前用户**，展开**个人**，然后单击**证书**。  

2.  右键单击**Fabrikam 加密**证书，依次指向**的所有任务**，然后单击**导出**。  

3.  上**欢迎使用证书导出向导**页上，单击**下一步**。  

4.  上**导出私钥**页上，选择**否，不导出私钥**，然后单击**下一步**。  

5.  上**导出文件格式**页上，单击**下一步**。  

6.  上**文件导出**页上，单击**浏览**。  

7.  在另存为对话框中，输入**\<驱动器\>: \Certs**有关**中保存**， **Fabrikam Public Encryption.cer**作为**文件名称**，并 **\*.cer**有关**另存为类型**，然后单击**保存**。  

8.  上**导出的文件**页上，单击**下一步**。  

9. 上**正在完成证书导出向导**页上，单击**完成**。  

10. 在指示导出成功证书导出向导弹出窗口中，单击**确定**。  

11. 对于“Fabrikam 签名”证书，请重复步骤 1 到步骤 9，并使用 Fabrikam Public Signature.cer 文件名。  

12. 对于“Contoso 签名”证书和“Contoso 加密”证书，请分别重复步骤 1 到步骤 9，并分别使用 Contoso Public Signature.cer 和 Contoso Public Encryption.cer 文件名。  

## <a name="see-also"></a>请参阅  
 [步骤 3：导入公共和私有证书](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)