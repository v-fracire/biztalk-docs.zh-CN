---
title: 使用配置框架 |Microsoft 文档
ms.custom: ''
ms.date: 2015-10-28
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18ec869d-6e81-42f5-9961-29b06e03fa54
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc5360cf5e76bfc6218f0fe54444b1651afdefae
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976619"
---
# <a name="working-with-the-configuration-framework"></a>使用配置框架
通过配置框架，可在安装时轻松快速地更改 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配置。 通过与 Microsoft Windows Installer (MSI) 结合使用，配置框架可以读取并报告计算机的状态和需要操作的配置任务。  
  
 在使用配置向导首次配置 BizTalk Server 时，配置框架将生成一个 XML 文件（配置快照），您随后可对该文件进行修改（即更改用户名、密码等）并将其导出到其他计算机。 您可在“配置摘要”页（配置向导的一部分）上保存配置快照。 您还可使用此快照将配置作为脚本安装的一部分进行复制。 此文件位于\< *BizTalk 安装路径*\>\ConfigMain.xml。  
  
> [!NOTE]
>  该 XML 文件中不存储密码。 使用此文件之前，必须输入密码。  
  
## <a name="configuration-framework-command-line-parameters"></a>配置框架命令行参数  
 下表说明了可以在配置框架中通过命令行运行的参数：  
  
|命令行参数|说明|  
|----------------------------|-----------------|  
|**/U**|取消对所有功能的配置。 **注意：** 取消对 BizTalk Server 功能的配置后，可删除 BizTalk Server 数据库。 请不要在运行此命令之前删除 BizTalk Server 数据库。 **注意：** 如果要在取消对 BizTalk Server 功能的配置后，删除 BizTalk Server 数据库，建议使用  **net stop winmgmt** 命令停止可能仍在运行的 Windows 管理规范 (WMI) 服务。|  
|**/S**|无提示配置。<br /><br /> 您还必须提供包含要安装和配置的功能的配置 XML 的完整路径。 如果没有传递 **/s**，则该工具将以用户界面 (UI) 模式运行。|  
|**/L**|-   设置日志文件的完整路径（可选）。|  
|**/H**|-   显示有效的命令行参数。|  
  
## <a name="sample-configuration-xml-file"></a>示例配置 XML 文件  
 下面是一个示例配置 XML 文件，其中安装了所有功能。 若要创建自己的配置文件，请使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上的自定义配置选项，确认所有组件已成功完成，然后在“配置”窗口中，选择“导出配置”。 然后可使用导出的配置文件来配置其他的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
```  
<Configuration>  
  <Feature Name="SSOServer,Engine" DisplayName="Enterprise Single Sign-On" Version="1.0" Description="Enterprise Single Sign-On configuration" ConfigByDefault="true">  
    <Question ID="IsSecretServer" Text="&Create a new SSO system;&Join an existing SSO system" Answers="Create,Join" Default="Create">  
      <Answer Value="Create" GUID="{FB7268BE-82D4-4cad-8CFF-6930303DA7E2}" Selected="Yes">  
        <NTCredential ID="SSOAdminGroup" DisplayName="SSO Administrator(s)" Description="This is the Administrator of the Enterprise Single Sign-On (SSO) system.">  
          <NTAccount ScopeType="105" UpLevelFlags="672" DownLevelFlags="2147516422" />  
        </NTCredential>  
        <NTCredential ID="SSOAffiliateAdminGroup" DisplayName="SSO Affiliate Administrator(s)" Description="The SSO Affiliate Administrator must be able to create Affiliate Applications.">  
          <NTAccount ScopeType="105" UpLevelFlags="672" DownLevelFlags="2147516422" />  
        </NTCredential>  
        <FILE ID="SSO_ID_BACKUP_SECRET_FILE" DisplayName="&Backup file location:" Filter="Backup files (*.bak)|*.bak|All files (*.*)|*.*" DefaultExtension="bak" Title="" Description="Location where the master secret will be backed up" OpenFile="true">  
          <Value />  
        </FILE>  
        <Name ID="SSO_ID_BACKUP_SECRET_PASSWORD" DisplayName="&Secret backup password:" Description="Enter a password used to protect the secret backup file" Hidden="true">  
          <Value>  
          </Value>  
        </Name>  
        <Name ID="SSO_ID_BACKUP_SECRET_PASSWORD_CONFIRM" DisplayName="&Confirm password:" Description="Confirm the secret backup password" Hidden="true">  
          <Value>  
          </Value>  
        </Name>  
        <Name ID="SSO_ID_BACKUP_SECRET_REMINDER" DisplayName="Password &reminder:" Description="Enter a phrase to help you remember the secret backup file password" Hidden="false">  
          <Value />  
        </Name>  
      </Answer>  
      <Answer Value="Join" GUID="{B9432756-1620-4bec-8CD9-E6D0B7805AA5}" />  
    </Question>  
    <NTService ID="ENTSSO" DisplayName="Enterprise Single Sign-On Service" Description="Specify the name of the account under which the Single Sign-On (SSO) service should run. This account must be a member of the SSO Administrator(s) group.">  
      <UserName>ServiceAccountName</UserName>  
      <Domain>Enter your domain name</Domain>  
      <Password />  
    </NTService>  
    <SQL ID="SSO_DB_ID" DisplayName="SSO Database" Description="Specify the name of the SQL Server and Database that will be used as the credential store.">  
      <Server>Enter your SQL Server name</Server>  
      <Database>SSODB</Database>  
      <WindowsSecurity Editable="no">yes</WindowsSecurity>  
      <UserName />  
      <Password />  
    </SQL>  
  </Feature>  
  <Feature Name="WMI" DisplayName="BizTalk Server Group" Version="1.0" Description="The Microsoft Windows Management Instrumentation (WMI) layer encapsulates all administrative functions and management capabilities for BizTalk Server." ConfigByDefault="true">  
    <SQL ID="{D757DBF9-5D71-4995-9F20-A552B7DFE7F1}" DisplayName="BizTalk Management Database" Description="This database is the central meta-information store for all BizTalk Servers.">  
      <Server>Enter your SQL Server name</Server>  
      <Database>BizTalkMgmtDb</Database>  
      <WindowsSecurity Editable="no">yes</WindowsSecurity>  
      <UserName />  
      <Password />  
    </SQL>  
    <Question ID="CREATEORJOIN" Text="Create a &new BizTalk Group;&Join an existing BizTalk Group" Answers="Create,Join" Default="Create">  
      <Answer Value="Create" GUID="{C4DEF4B8-163E-4a8d-AB01-6C43917248B1}" Selected="Yes">  
        <SQL ID="{84ADD76E-EBEB-4bb8-B9EB-64F87E483C39}" DisplayName="BizTalk MessageBox Database" Description="This database stores subscriptions predicates. It is a host platform, where the queues and state tables for each BizTalk Server host are kept. The MessageBox database also stores the messages and message properties.">  
          <Server>Enter your SQL Server name</Server>  
          <Database>BizTalkMsgBoxDb</Database>  
          <WindowsSecurity Editable="no">yes</WindowsSecurity>  
          <UserName />  
          <Password />  
        </SQL>  
        <SQL ID="{1033195A-3C23-4750-BBD0-06BC12A175D4}" DisplayName="BizTalk Tracking Database" Description="This database stores business and health monitoring data tracked by the BizTalk Server tracking engine.">  
          <Server>Enter your SQL Server name</Server>  
          <Database>BizTalkDTADb</Database>  
          <WindowsSecurity Editable="no">yes</WindowsSecurity>  
          <UserName />  
          <Password />  
        </SQL>  
        <NTCredential ID="BTS_ADMIN_GROUP" DisplayName="BizTalk Administrators Group" Description="The BizTalk Server Administrators Group has the least privileges necessary to perform administrative tasks included in the Configuration Framework Wizard and to administer the BizTalk Server environment after installation.">  
          <NTAccount ScopeType="105" UpLevelFlags="672" DownLevelFlags="2147483654">BizTalk Server Administrators</NTAccount>  
        </NTCredential>  
        <NTCredential ID="BTS_OPERATOR_GROUP" DisplayName="BizTalk Operators Group" Description="The BizTalk Server Operators Group has the least privileges necessary to perform tasks required for operating the BizTalk Server environment after installation.">  
          <NTAccount ScopeType="105" UpLevelFlags="672" DownLevelFlags="2147483654">BizTalk Server Operators</NTAccount>  
        </NTCredential>  
        <NTCredential ID="BTS_B2B_OPERATOR_GROUP" DisplayName="BizTalk B2B Operators Group" Description="The BizTalk Server B2B Operators Group has the least privileges necessary to perform tasks required for operating the BizTalk Server B2B environment after installation.">  
          <NTAccount ScopeType="105" UpLevelFlags="672" DownLevelFlags="2147483654">BizTalk Server B2B Operators</NTAccount>  
        </NTCredential>  
      </Answer>  
      <Answer Value="Join" GUID="{4D12E6A3-552E-4936-9DD3-59E1190FA324}" />  
    </Question>  
  </Feature>  
  <Feature Name="Engine,BTSCfg" DisplayName="BizTalk Server runtime components" Version="1.0" Description="These settings determine the manner in which the BizTalk hosts and host instances are created." ConfigByDefault="true">  
    <Question ID="HOST" Text="&Create In-Process Host and Instance" Answers="Yes,No" Default="Yes">  
      <Answer Value="Yes" GUID="{8E714C78-05B8-45d1-9B50-D737EF7AD682}" Selected="Yes">  
        <Question ID="TRUSTEDHOST" Text="&Trusted" Answers="Yes,No" Default="No">  
          <Answer Value="Yes" GUID="{D460CE6D-CCF1-4ebf-BDC9-3149021B91ED}" />  
          <Answer Value="No" GUID="{F507BD3D-2205-47bc-A7EF-0E45603BB6C4}" Selected="Yes" />  
        </Question>  
        <Question ID="GENERICHOST" Text="32-bit on&ly" Answers="Yes,No" Default="Yes">  
          <Answer Value="Yes" GUID="{5D3B2217-D744-4D50-B931-FED9E259628D}" Selected="Yes" />  
          <Answer Value="No" GUID="{CBF077AE-2771-473E-9E0C-D955D5EB5692}" />  
        </Question>  
        <NTCredential ID="BTS_HOST_GROUP" DisplayName="BizTalk Host Users Group" Description="Windows group for accounts with access to the In-Process BizTalk  hosts (hosts processes in the BizTalk Server).">  
          <NTAccount ScopeType="105" UpLevelFlags="672" DownLevelFlags="2147483654">BizTalk Application Users</NTAccount>  
        </NTCredential>  
        <Name ID="BTS_HOST_NAME" DisplayName="Ho&st name:" Description="Name of the In-Process BizTalk  host (eg, BizTalkServerApplication)" Hidden="false">  
          <Value>BizTalkServerApplication</Value>  
        </Name>  
        <NTService ID="{B64F63FA-E24E-4991-86F0-ED9F65B68A98}" DisplayName="BizTalk Host Instance Account" Description="Windows account with access to a specific In-Process BizTalk host instance. This account will be given Log on as Service rights.">  
          <UserName>ServiceAccountName</UserName>  
          <Domain />  
          <Password>  
          </Password>  
        </NTService>  
      </Answer>  
      <Answer Value="No" GUID="{D9164C48-8179-4a40-912D-1BF4C3EFE70B}" />  
    </Question>  
    <Question ID="ISOHOST" Text="Cr&eate Isolated Host and Instance" Answers="Yes,No" Default="Yes">  
      <Answer Value="Yes" GUID="{5638D8B2-58C9-4b2a-B5B1-3771ADECC327}" Selected="Yes">  
        <Question ID="TRUSTEDIHOST" Text="Truste&d" Answers="Yes,No" Default="No">  
          <Answer Value="Yes" GUID="{D460CE6D-CCF1-4ebf-BDC9-3149021B91ED}" />  
          <Answer Value="No" GUID="{F507BD3D-2205-47bc-A7EF-0E45603BB6C4}" Selected="Yes" />  
        </Question>  
        <Question ID="GENERICIHOST" Text="32-bit onl&y" Answers="Yes,No" Default="Yes">  
          <Answer Value="Yes" GUID="{5D3B2217-D744-4D50-B931-FED9E259628D}" Selected="Yes" />  
          <Answer Value="No" GUID="{CBF077AE-2771-473E-9E0C-D955D5EB5692}" />  
        </Question>  
        <NTCredential ID="BTS_IHOST_GROUP" DisplayName="BizTalk Isolated Host Users Group" Description="Windows group for accounts with access to the Isolated BizTalk hosts (hosts processes not running on BizTalk Server, such as HTTP and SOAP)">  
          <NTAccount ScopeType="105" UpLevelFlags="672" DownLevelFlags="2147483654">BizTalk Isolated Host Users</NTAccount>  
        </NTCredential>  
        <Name ID="BTS_IHOST_NAME" DisplayName="Is&olated Host name:" Description="Name of the Isolated BizTalk host (eg BizTalkServerIsolatedHost)" Hidden="false">  
          <Value>BizTalkServerIsolatedHost</Value>  
        </Name>  
        <NTService ID="{D0A37CEE-F24E-4193-A19F-47B05D7EDA21}" DisplayName="BizTalk Isolated Host Instance Account" Description="Windows account with access to a specific Isolated BizTalk  host instance. This account will be given Log on as Service rights.">  
          <UserName>ServiceAccountName</UserName>  
          <Domain />  
          <Password>  
          </Password>  
        </NTService>  
      </Answer>  
      <Answer Value="No" GUID="{5782A1A5-8578-4942-9CBB-E443A15A0B99}" />  
    </Question>  
  </Feature>  
  <Feature Name="RulesEngine" DisplayName="Business Rules Engine" Version="3.0" Description="BizTalk native support for declarative Business Rules." ConfigByDefault="true">  
    <SQL ID="{E6C5E071-D6EB-4c31-BFE6-CA16637FBEEB}" DisplayName="Rule Engine Database" Description="SQL Rule Store">  
      <Server>Enter your SQL Server name</Server>  
      <Database>BizTalkRuleEngineDb</Database>  
      <WindowsSecurity>yes</WindowsSecurity>  
      <UserName />  
      <Password />  
    </SQL>  
    <NTService ID="{6ABAD351-9C7B-423e-9FDE-3A5C52441C00}" DisplayName="Rule Engine Update Service" Description="Notification for the deployment/ undeployment of policies">  
      <UserName>domain\ServiceAccountName</UserName>  
      <Domain />  
      <Password>  
      </Password>  
    </NTService>  
  </Feature>  
  <Feature Name="MOT" DisplayName="BAM runtime" Version="1.0" Description="Tracking data decoding service used to move tracked data and persist it for query use." />  
  <Feature Name="BAMTools" DisplayName="Business Activity Monitoring tools" Version="1.0" Description="Tools for  the creation and maintenance of the SQL Server and Analysis Server (OLAP) infrastructure for Business Activity Monitoring." ConfigByDefault="true">  
    <SQL ID="{E1FC3106-8DD4-4f12-9EB6-849DD8BDD605}" DisplayName="BAM Primary Import Database" Description="SQL database used to store the events from the Business Activities and then query for the progress and data of the activity instances. This database is also used for real-time aggregations.">  
      <Server>Enter your SQL Server name</Server>  
      <Database>BAMPrimaryImport</Database>  
      <WindowsSecurity Editable="no">yes</WindowsSecurity>  
      <UserName />  
      <Password />  
    </SQL>  
    <SQL ID="{1D372BCB-DF59-43b6-A4A9-87082B5727B0}" DisplayName="BAM Archive Database" Description="SQL database used for archiving the Business Activity data which is too old. It is recommended to create the BAM Archive database to minimize the accumulation of Business Activity data in the BAM Primary Import Database.">  
      <Server>Enter your SQL Server name</Server>  
      <Database>BAMArchive</Database>  
      <WindowsSecurity Editable="no">yes</WindowsSecurity>  
      <UserName />  
      <Password />  
    </SQL>  
    <Question ID="{12A38787-6B24-40ab-8888-5FE8ABA87B26}" Text="Enable A&nalysis Services for BAM aggregations" Answers="Yes,No" Default="No">  
      <Answer Value="Yes" GUID="{902F7E20-D6AE-453f-9D23-935ED7AF94C3}">  
        <SQL ID="{16567D1E-6946-4f4e-BB3F-900DE2648328}" DisplayName="BAM Analysis Database" Description="Analysis Services database that keeps the aggregated historical data for Business Activities" MSOLAPServer="Yes">  
          <Server>Enter your SQL Server name</Server>  
          <Database>BAMAnalysis</Database>  
          <WindowsSecurity Editable="no">yes</WindowsSecurity>  
          <UserName />  
          <Password />  
        </SQL>  
        <SQL ID="{B973DB76-BA7F-4a2e-A57E-07EEF54B37A8}" DisplayName="BAM Star Schema Database" Description="SQL database used to transform the data collected from the Business Activity Monitoring for OLAP Processing. This database is required when the BAM Analysis database is used.">  
          <Server>Enter your SQL Server name</Server>  
          <Database>BAMStarSchema</Database>  
          <WindowsSecurity Editable="no">yes</WindowsSecurity>  
          <UserName />  
          <Password />  
        </SQL>  
      </Answer>  
      <Answer Value="No" GUID="{FC612DFE-1273-4f57-8EE3-95216638A67B}" Selected="Yes" />  
    </Question>  
    <Question ID="{308cc88b-9e51-4103-ae4c-73300e02a7eb}" Text="&Enable BAM alerts" Answers="Yes,No" Default="No">  
      <Answer Value="Yes" GUID="{458e1878-eae6-4e09-8e5c-ba516548ceac}">  
        <Name ID="{8B3212A1-44EA-46bc-A06C-75E289D1F840}" DisplayName="S&QL Server for Alerts Databases:" Description="Notification Services server for BAM Alerting." Hidden="false">  
          <Value>Enter your SQL Server name</Value>  
        </Name>  
        <Name ID="{1DAFDF2D-4377-415a-B1CA-2C5B3729A244}" DisplayName="Prefix for Alerts Database &Names:" Description="Notification Services database root name for BAM Alerting." Hidden="false">  
          <Value>BAMAlerts</Value>  
        </Name>  
        <NTService ID="{c116ba3f-06d0-48cf-b0a1-4b263b07250e}" DisplayName="BAM Alerts User" Description="Windows account that will have permissions to access the data in the BAM Notification Services databases during Business Activity searches.">  
          <UserName />  
          <Domain />  
          <Password />  
        </NTService>  
        <Name ID="{33c8fd0a-c89d-4dd0-8b2b-2ddacc6620e6}" DisplayName="BAM Alerts &SMTP Server:" Description="SMTP server to use for sending out BAM Alerting messages." Hidden="false">  
          <Value>Enter your server name</Value>  
        </Name>  
        <Name ID="{335b35f5-ffc4-4c7e-8cfc-582ec6bab9e0}" DisplayName="BAM Alerts File &Location:" Description="File system location to use for writing out BAM Alerting messages.  If you accept this default location for delivering alerts by file, Configuration will create the file share and grant write permissions to the SQL NS service account and the current logged-on user." Hidden="false">  
          <Value>\\Enter your server name\alerts</Value>  
        </Name>  
      </Answer>  
      <Answer Value="No" GUID="{3d95a679-aa37-403f-bf64-194e6aa2d993}" Selected="Yes" />  
    </Question>  
    <Question ID="{FC99D786-2D26-489b-A748-42AE4DD0F6FC}" Text="&Remove the Business Activity Monitoring tools for this Biztalk Group" Answers="Yes,No" Default="No">  
      <Answer Value="Yes" GUID="{4CF85429-F0DA-4ca3-8068-D125506A3FD9}" />  
      <Answer Value="No" GUID="{5823E008-032F-4917-9EE5-B0AB4A18325C}" Selected="Yes" />  
    </Question>  
  </Feature>  
  <Feature Name="BAMPortal" DisplayName="BAM Portal" Version="1.0" Description="The Business Activity Monitoring (BAM) Portal is used to query individual instance data stored in the Tracking database. Each BAM Query Web Service corresponds to one SQL database." ConfigByDefault="true">  
    <NTService ID="{C08C5A6C-53FB-41bd-A1CE-FD7209FD16F4}" DisplayName="BAM Management Web Service user" Description="Windows account that will have permissions to access the data in the BAM Primary Import Database during Business Activity searches.">  
      <UserName>ServiceAccountName</UserName>  
      <Domain>Enter your domain name</Domain>  
      <Password>  
      </Password>  
    </NTService>  
    <NTService ID="{FAAB0AD8-C414-4735-91E5-3DCEC8CB96A8}" DisplayName="BAM Application Pool Account" Description="Identity of the BAM Application Pool. ">  
      <UserName>ServiceAccountName</UserName>  
      <Domain>Enter your domain name</Domain>  
      <Password>  
      </Password>  
    </NTService>  
    <NTCredential ID="{e8118b16-0585-41a4-99bb-6d8a30570fcc}" DisplayName="BAM Portal Users" Description="The user accounts under which the BAM portal services run.">  
      <NTAccount ScopeType="103" UpLevelFlags="676" DownLevelFlags="2147483654">Everyone</NTAccount>  
    </NTCredential>  
    <WebSite ID="{DA1ABC72-465B-4953-ADD7-98CEA6F4E503}" DisplayName="BAM Portal Web &Site:" Description="Specify the name of the web site under which the BAM Portal virtual directory will be created.">  
      <WebSiteName>Default Web Site</WebSiteName>  
    </WebSite>  
  </Feature>  
  <Feature Name="MsEDIAS2" DisplayName="BizTalk EDI/AS2 Runtime" Version="1.0" Description="The EDI Runtime enables BizTalk Server to process EDI documents." ConfigByDefault="true">  
    <Question ID="EDI" Text="E&nable BizTalk EDI for this BizTalk Group" Answers="Yes,No" Default="Yes">  
      <Answer Value="Yes" GUID="{EC1CDD3A-BFD2-48A1-92B5-45F3069DE061}" Selected="Yes" />  
      <Answer Value="No" GUID="{7FF0780D-406C-4BCC-BC77-A5BD83869193}" />  
    </Question>  
    <Question ID="AS2" Text="Ena&ble BizTalk AS2 for this BizTalk Group" Answers="Yes,No" Default="Yes">  
      <Answer Value="Yes" GUID="{2E33F8AA-4126-4608-9344-7B8EBDE78E29}" Selected="Yes" />  
      <Answer Value="No" GUID="{DEC87603-0372-4ACC-B567-15BA6AFE630E}" />  
    </Question>  
    <Question ID="StatusReport" Text="Enable BizTalk EDI/AS2 Runtime &Status Reporting for this BizTalk Group" Answers="Yes,No" Default="Yes">  
      <Answer Value="Yes" GUID="{6A273C7A-67FC-40FE-ADB7-FF41CD682021}" Selected="Yes" />  
      <Answer Value="No" GUID="{09DC7E6A-BE35-4C58-BC12-E04403F613AA}" />  
    </Question>  
    <Question ID="RemoveEDI" Text="&Remove BizTalk EDI, AS2, and Status Reporting functionalities from this BizTalk Group" Answers="Yes,No" Default="No">  
      <Answer Value="Yes" GUID="{18C53BC3-38B6-4014-AD32-34552A044181}" />  
      <Answer Value="No" GUID="{DC2362B1-10E0-4EDC-9710-CC27A73090C5}" Selected="Yes" />  
    </Question>  
  </Feature>  
  <InstalledFeature>MsEDIAS2</InstalledFeature>  
  <InstalledFeature>MsEDIAS2StatusReporting</InstalledFeature>  
  <InstalledFeature>WCFAdapter</InstalledFeature>  
  <InstalledFeature>InfoWorkerApps</InstalledFeature>  
  <InstalledFeature>BAMPortal</InstalledFeature>  
  <InstalledFeature>WcfAdapterAdminTools</InstalledFeature>  
  <InstalledFeature>PAM</InstalledFeature>  
  <InstalledFeature>Documentation</InstalledFeature>  
  <InstalledFeature>WMI</InstalledFeature>  
  <InstalledFeature>BizTalk</InstalledFeature>  
  <InstalledFeature>MOT</InstalledFeature>  
  <InstalledFeature>Engine</InstalledFeature>  
  <InstalledFeature>MSMQ</InstalledFeature>  
  <InstalledFeature>Runtime</InstalledFeature>  
  <InstalledFeature>RfidEventForwarderMessageTransform</InstalledFeature>  
  <InstalledFeature>AdminAndMonitoring</InstalledFeature>  
  <InstalledFeature>MonitoringAndTracking</InstalledFeature>  
  <InstalledFeature>AdminTools</InstalledFeature>  
  <InstalledFeature>BizTalkAdminSnapIn</InstalledFeature>  
  <InstalledFeature>HealthActivityClient</InstalledFeature>  
  <InstalledFeature>BAMTools</InstalledFeature>  
</Configuration>  
```  
  
## <a name="see-also"></a>另请参阅  
 [配置 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)   