# @ohos.dlpPermission

数据防泄漏（Data Loss Prevention，简称为DLP）是系统级的数据防泄漏解决方案，提供跨设备文件的权限管理、加密存储、授权访问等能力。DLP通过加密技术对敏感文件进行保护，生成.dlp格式的加密文件（称为DLP文件）。
当打开DLP文件时，系统会自动创建隔离的DLP沙箱环境，确保文件内容不会泄漏到非授权环境。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - @ohos.dlpPermission归属的Kit已由`DataLossPreventionKit`变更为`DataProtectionKit`，建议开发者使用新模块名`@kit.DataProtectionKit`完成模块导
> 入。如果使用`@kit.DataLossPreventionKit`导入，仅能调用改名前的接口，无法使用新增接口。

**起始版本：** 10

**系统能力：** SystemCapability.Security.DataLossPrevention

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancelRetentionState](arkts-dataprotection-dlppermission-cancelretentionstate-f.md#cancelRetentionState-1) | 取消沙箱保留状态即恢复DLP文件关闭时自动卸载沙箱策略。使用Promise异步回调。<br/><br/>该接口用于取消沙箱保留状态，恢复默认行为以释放系统资源，适用于不再频繁访问DLP文件的场景。<br/> |
| [cancelRetentionState](arkts-dataprotection-dlppermission-cancelretentionstate-f.md#cancelRetentionState-2) | 取消沙箱保留状态即恢复DLP文件关闭时自动卸载沙箱策略。使用callback异步回调。<br/><br/>该接口用于取消沙箱保留状态，恢复默认行为以释放系统资源，适用于不再频繁访问DLP文件的场景。<br/> |
| [cleanSandboxAppConfig](arkts-dataprotection-dlppermission-cleansandboxappconfig-f.md#cleanSandboxAppConfig-1) | 清理沙箱应用配置信息。调用成功后，沙箱应用配置将被清除，恢复默认状态。使用Promise异步回调。<br/><br/>该接口用于清理沙箱应用的配置信息，恢复默认状态以防止配置残留影响后续使用。<br/> |
| [closeOpenedEnterpriseDlpFiles](arkts-dataprotection-dlppermission-closeopenedenterprisedlpfiles-f.md#closeOpenedEnterpriseDlpFiles-1) | 关闭当前打开的所有符合指定选项的企业DLP文件。使用Promise异步回调。<br/><br/>在需要批量关闭企业DLP文件、清理文件资源或应用退出前释放文件句柄时调用该接口。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口仅能关闭调用方应用通过[generateDlpFileForEnterprise](arkts-dataprotection-dlppermission-generatedlpfileforenterprise-f-sys.md#generateDlpFileForEnterprise-1)生成的企业DLP文件。<br/> |
| <!--DelRow-->[decryptDlpFile](arkts-dataprotection-dlppermission-decryptdlpfile-f-sys.md#decryptDlpFile-1) | 将DLP文件解密生成明文文件，仅支持企业账号调用。使用Promise异步回调。<br/><br/>该接口用于将DLP加密文件解密为明文文件，适用于拥有者权限用户导出或迁移文件。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口仅支持企业账号调用，需要企业自行搭建企业账号服务器配套使用。由企业服务器管控账号是否有权限解密DLP文件。<br/> |
| <!--DelRow-->[generateDLPFile](arkts-dataprotection-dlppermission-generatedlpfile-f-sys.md#generateDLPFile-1) | DLP管理应用调用该接口，将明文文件加密生成DLPFile管理对象，对象仅在授权列表内的用户可以打开，授权又分为完全控制权限和只读权限。使用Promise异步回调。<br/><br/>调用generateDLPFile成功后返回DLPFile对象，必须在使用完毕后调用closeDLPFile释放资源。<br/> |
| <!--DelRow-->[generateDLPFile](arkts-dataprotection-dlppermission-generatedlpfile-f-sys.md#generateDLPFile-2) | DLP管理应用调用该接口，将明文文件加密生成权限受控文件，仅在授权列表内的用户可以打开，授权又分为完全控制权限和只读权限。获取DLPFile管理对象，使用callback异步回调。使用完DLPFile对象后，应调用<br/>closeDLPFile释放对象，避免资源泄露。<br/><br/>调用generateDLPFile()成功后返回DLPFile对象，必须在使用完毕后调用closeDLPFile()释放资源。<br/> |
| <!--DelRow-->[generateDlpFileForEnterprise](arkts-dataprotection-dlppermission-generatedlpfileforenterprise-f-sys.md#generateDlpFileForEnterprise-1) | 将明文文件加密生成企业账号DLP文件，仅支持企业账号调用。使用Promise异步回调。<br/><br/>用于将明文文件加密生成企业账号的DLP权限受控文件，实现企业级的文件权限管理。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口仅支持企业账号调用，需要企业自行搭建企业账号服务器配套使用。使用该接口可以将明文文件加密生成权限受控文件，由企业服务器管控账号是否有权限解密该文件。<br/> |
| [getDLPFileAccessRecords](arkts-dataprotection-dlppermission-getdlpfileaccessrecords-f.md#getDLPFileAccessRecords-1) | 查询最近访问的DLP文件列表。调用成功后返回文件访问记录，用于追踪和管理DLP文件的使用情况。仅支持在非DLP沙箱应用中调用。使用Promise异步回调。<br/><br/>该接口用于获取最近访问的DLP文件记录列表，便于审计追踪和文件使用情况管理。<br/> |
| [getDLPFileAccessRecords](arkts-dataprotection-dlppermission-getdlpfileaccessrecords-f.md#getDLPFileAccessRecords-2) | 查询最近访问的DLP文件列表。调用成功后返回文件访问记录，用于追踪和管理DLP文件的使用情况。使用callback异步回调。<br/><br/>该接口用于获取最近访问的DLP文件记录列表，便于审计追踪和文件使用情况管理。<br/> |
| <!--DelRow-->[getDLPGatheringPolicy](arkts-dataprotection-dlppermission-getdlpgatheringpolicy-f-sys.md#getDLPGatheringPolicy-1) | 查询DLP沙箱聚合策略。使用Promise异步回调。<br/><br/>应用需要获取当前系统的DLP沙箱聚合策略配置时使用此接口。<br/> |
| <!--DelRow-->[getDLPGatheringPolicy](arkts-dataprotection-dlppermission-getdlpgatheringpolicy-f-sys.md#getDLPGatheringPolicy-2) | 查询DLP沙箱聚合策略。使用callback异步回调。<br/><br/>应用需要获取当前系统的DLP沙箱聚合策略配置时使用此接口。<br/> |
| [getDLPPermissionInfo](arkts-dataprotection-dlppermission-getdlppermissioninfo-f.md#getDLPPermissionInfo-1) | 查询当前DLP沙箱的权限信息，包括文件授权类型及可执行操作（如查看、编辑、复制等）。仅支持在DLP沙箱应用中调用，使用Promise异步回调。<br/><br/>在DLP沙箱中处理文件时，可根据权限信息判断当前用户可以执行哪些操作，避免调用无权限的功能。<br/> |
| [getDLPPermissionInfo](arkts-dataprotection-dlppermission-getdlppermissioninfo-f.md#getDLPPermissionInfo-2) | 查询当前DLP沙箱的权限信息。返回的权限信息包括文件的授权类型和可执行的操作权限(如查看、编辑、复制等)。使用callback异步回调。<br/><br/>在DLP沙箱中处理文件时，可根据权限信息判断当前用户可以执行哪些操作，避免调用无权限的功能。<br/> |
| [getDLPSuffix](arkts-dataprotection-dlppermission-getdlpsuffix-f.md#getDLPSuffix-1) | 获取DLP文件扩展名。调用成功后返回DLP文件扩展名（如'.dlp'）。接口为同步接口。<br/><br/>用于获取DLP文件的标准扩展名，便于构建DLP文件名或进行文件类型判断。<br/> |
| [getDLPSupportedFileTypes](arkts-dataprotection-dlppermission-getdlpsupportedfiletypes-f.md#getDLPSupportedFileTypes-1) | 查询当前可支持权限设置和校验的文件扩展名类型列表。调用成功后返回支持的文件类型列表，用于判断哪些文件类型可进行DLP权限管理。使用Promise异步回调。<br/><br/>该接口用于获取支持DLP权限管理的文件类型列表，以便决定当前文件是否可以进行加密。<br/> |
| [getDLPSupportedFileTypes](arkts-dataprotection-dlppermission-getdlpsupportedfiletypes-f.md#getDLPSupportedFileTypes-2) | 查询当前可支持权限设置和校验的文件扩展名类型列表。调用成功后返回支持的文件类型列表，用于判断哪些文件类型可进行DLP权限管理。使用callback异步回调。<br/><br/>该接口用于获取支持DLP权限管理的文件类型列表，以便决定当前文件是否可以进行加密。<br/> |
| [getOriginalFileName](arkts-dataprotection-dlppermission-getoriginalfilename-f.md#getOriginalFileName-1) | 获取指定DLP文件名的原始文件名。该接口为同步接口。<br/><br/>根据原始文件名后缀判断文件类型，选择对应的应用打开。<br/> |
| [getRetentionSandboxList](arkts-dataprotection-dlppermission-getretentionsandboxlist-f.md#getRetentionSandboxList-1) | 查询指定应用的保留沙箱信息列表。仅支持在非DLP沙箱应用中调用。使用Promise异步回调。<br/><br/>该接口用于查询指定应用的保留沙箱列表，以便查看或管理当前处于保留状态的沙箱环境。<br/> |
| [getRetentionSandboxList](arkts-dataprotection-dlppermission-getretentionsandboxlist-f.md#getRetentionSandboxList-2) | 查询指定应用的保留沙箱信息列表。使用callback异步回调。<br/><br/>该接口用于查询指定应用的保留沙箱列表，以便查看或管理当前处于保留状态的沙箱环境。<br/> |
| [getRetentionSandboxList](arkts-dataprotection-dlppermission-getretentionsandboxlist-f.md#getRetentionSandboxList-3) | 查询当前应用的保留沙箱信息列表。使用callback异步回调。<br/><br/>该接口用于查询指定应用的保留沙箱列表，以便查看或管理当前处于保留状态的沙箱环境。<br/> |
| [getSandboxAppConfig](arkts-dataprotection-dlppermission-getsandboxappconfig-f.md#getSandboxAppConfig-1) | 获取沙箱应用配置信息，使用Promise异步回调。<br/><br/>该接口用于获取沙箱应用的配置信息，便于读取或验证当前的配置状态。<br/> |
| <!--DelRow-->[installDLPSandbox](arkts-dataprotection-dlppermission-installdlpsandbox-f-sys.md#installDLPSandbox-1) | 安装一个应用的DLP沙箱。DLP沙箱为受保护的DLP文件创建独立的运行环境，与原应用进程隔离，确保数据在授权范围内安全流转。沙箱应用继承原应用的功能但仅能访问授权的DLP文件。使用Promise异步回调。<br/><br/>调用installDLPSandbox成功后必须在使用完毕后调用uninstallDLPSandbox卸载沙箱。<br/><br/>DLP文件管理应用打开受保护文件前，需要先为目标应用安装DLP沙箱。<br/> |
| <!--DelRow-->[installDLPSandbox](arkts-dataprotection-dlppermission-installdlpsandbox-f-sys.md#installDLPSandbox-2) | 安装一个应用的DLP沙箱。使用callback异步回调。调用成功后，系统为应用创建DLP沙箱环境并返回沙箱信息。<br/><br/>调用installDLPSandbox成功后必须在使用完毕后调用uninstallDLPSandbox卸载沙箱。<br/><br/>DLP文件管理应用打开受保护文件前，需要先为目标应用安装DLP沙箱。<br/> |
| [isDLPFeatureProvided](arkts-dataprotection-dlppermission-isdlpfeatureprovided-f.md#isDLPFeatureProvided-1) | 查询当前系统是否提供加密保护特性，仅支持企业设备且需[MDM（Mobile Device Management，移动设备管理）](../../../../mdm/mdm-kit-intro.md)配置使能。调用成功后返回查询结果，<br/>用于判断系统是否支持DLP加密功能。使用Promise异步回调。<br/><br/>该接口用于判断当前系统是否支持DLP加密功能，以便在不支持的设备上做兼容处理或功能降级。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口由[MDM](../../../../mdm/mdm-kit-intro.md)配置使能，且使能场景为企业设备。其他设备（如消费者终端设备）无需关注该接口，如若调用该接口，则返回值为false。<br/> |
| [isDLPFile](arkts-dataprotection-dlppermission-isdlpfile-f.md#isDLPFile-1) | 根据文件的fd，查询该文件是否是DLP文件。使用Promise异步回调。<br/><br/>在文件处理流程中，需要先判断文件是否为DLP文件，再决定后续处理策略（如是否需要通过DLP沙箱打开）。<br/> |
| [isDLPFile](arkts-dataprotection-dlppermission-isdlpfile-f.md#isDLPFile-2) | 根据文件的fd，查询该文件是否是DLP文件。调用成功后返回查询结果，true表示是DLP文件，false表示非DLP文件。使用callback异步回调。<br/><br/>在文件处理流程中，需要先判断文件是否为DLP文件，再决定后续处理策略（如是否需要通过DLP沙箱打开）。<br/> |
| [isInSandbox](arkts-dataprotection-dlppermission-isinsandbox-f.md#isInSandbox-1) | 查询当前应用是否运行在DLP沙箱环境。使用Promise异步回调。<br/><br/>该接口用于判断当前应用是否处于DLP沙箱环境，以便决定是否执行沙箱相关的操作或调用沙箱专用接口。<br/> |
| [isInSandbox](arkts-dataprotection-dlppermission-isinsandbox-f.md#isInSandbox-2) | 查询当前应用是否运行在DLP沙箱环境。使用callback异步回调。<br/><br/>该接口用于判断当前应用是否处于DLP沙箱环境，以便决定是否执行沙箱相关的操作或调用沙箱专用接口。<br/> |
| [off](arkts-dataprotection-dlppermission-off-f.md#off-1) | 取消监听打开DLP文件。仅支持在非DLP沙箱应用中调用。调用成功后，将不再接收DLP文件打开事件的通知。<br/><br/>该接口通常在页面销毁或不再需要监听时调用以释放资源。<br/> |
| <!--DelRow-->[off](arkts-dataprotection-dlppermission-off-f-sys.md#off-2) | 取消监听DLP沙箱卸载事件。调用成功后，应用不再接收DLP沙箱卸载事件的回调通知。<br/><br/>必须在调用on()注册监听后才能调用此方法取消监听。<br/><br/>DLP管理应用退出或不再需要追踪沙箱状态变化时，取消事件订阅以释放监听资源。<br/> |
| [on](arkts-dataprotection-dlppermission-on-f.md#on-1) | 监听打开DLP文件。调用成功后，当DLP文件被打开时会触发回调通知当前应用。仅支持在非DLP沙箱应用中调用。<br/><br/>当应用需要在DLP文件打开后执行特定操作(如记录日志、更新界面)时，可注册该监听。<br/> |
| <!--DelRow-->[on](arkts-dataprotection-dlppermission-on-f-sys.md#on-2) | 注册监听DLP沙箱卸载事件，用于感知沙箱环境的变化。注册成功后，当DLP沙箱被卸载时，系统会通过回调函数通知应用。<br/><br/>调用on()注册监听后，建议在不需要监听时调用off()取消监听释放资源。<br/><br/>DLP管理应用需要追踪沙箱的创建和销毁状态，以便维护沙箱列表或执行相关的清理操作。<br/> |
| <!--DelRow-->[openDLPFile](arkts-dataprotection-dlppermission-opendlpfile-f-sys.md#openDLPFile-1) | DLP管理应用调用该接口，打开DLP文件。调用成功后返回DLPFile管理对象，可用于管理DLP文件的权限和进行相关操作。使用Promise异步回调。<br/><br/>调用openDLPFile()成功后返回DLPFile对象，必须在使用完毕后调用closeDLPFile释放资源。<br/><br/>DLP管理应用或授权应用需要访问受保护的DLP文件内容时，先打开文件获取管理对象。<br/> |
| <!--DelRow-->[openDLPFile](arkts-dataprotection-dlppermission-opendlpfile-f-sys.md#openDLPFile-2) | DLP管理应用调用该接口，打开DLP文件。使用callback异步回调。调用成功后返回DLPFile管理对象，可用于管理DLP文件的权限和进行相关操作。使用完DLPFile对象后，应调用closeDLPFile释放对象，避免资<br/>源泄露。<br/> |
| <!--DelRow-->[queryDlpPolicy](arkts-dataprotection-dlppermission-querydlppolicy-f-sys.md#queryDlpPolicy-1) | 在DLP文件中解析文件头，获取DLP明文策略。返回的策略JSON字符串包含[DLPProperty](arkts-dataprotection-dlppermission-dlpproperty-i.md#DLPProperty)和<br/>[CustomProperty](arkts-dataprotection-dlppermission-customproperty-i.md#CustomProperty)信息。使用Promise异步回调。<br/><br/>该接口可用于在查看DLP文件权限配置等场景中，获取文件的策略信息以便进行分析。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口仅支持企业账号调用<br/> |
| [queryOpenedEnterpriseDlpFiles](arkts-dataprotection-dlppermission-queryopenedenterprisedlpfiles-f.md#queryOpenedEnterpriseDlpFiles-1) | 查询已打开且符合指定选项的企业DLP文件的URI列表。使用Promise异步回调。<br/><br/>在需要管理或追踪当前应用已打开的企业DLP文件时调用该接口，可用于文件状态检查、资源管理等场景。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 该接口仅能查询调用方应用通过[generateDlpFileForEnterprise](arkts-dataprotection-dlppermission-generatedlpfileforenterprise-f-sys.md#generateDlpFileForEnterprise-1)生成的企业DLP文件，无法查询<br/>&gt; 其他应用生成的企业DLP文件。<br/>&gt;<br/>&gt; - 相同分类标签的只读企业DLP文件在同一个沙箱中打开。如果一个沙箱中打开了多个相同标签的只读企业DLP文件，则查询结果返回所有该沙箱打开过文件的URI（包括手动关闭的文件）。<br/> |
| [setEnterprisePolicy](arkts-dataprotection-dlppermission-setenterprisepolicy-f.md#setEnterprisePolicy-1) | 设置企业应用防护策略。调用成功后，企业应用的DLP防护将按照设置的策略执行。<br/><br/>该接口可用于企业管理员配置DLP安全策略，以统一管理企业数据安全防护规则。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口仅支持企业账号调用。<br/> |
| [setRetentionState](arkts-dataprotection-dlppermission-setretentionstate-f.md#setRetentionState-1) | 设置DLP沙箱的保留状态。默认情况下，打开DLP文件时系统会自动创建沙箱环境，关闭文件后自动销毁沙箱。设置保留状态后，即使关闭DLP文件，沙箱环境也会保留，便于快速重新打开相同DLP文件。适用于需要频繁操作同一DLP文件的场景<br/>，可提升文件打开效率。使用Promise异步回调。<br/> |
| [setRetentionState](arkts-dataprotection-dlppermission-setretentionstate-f.md#setRetentionState-2) | 设置DLP沙箱的保留状态。默认情况下，打开DLP文件时系统会自动创建沙箱环境，关闭文件后自动销毁沙箱。设置保留状态后，即使关闭DLP文件，沙箱环境也会保留，便于快速重新打开相同DLP文件。适用于需要频繁操作同一DLP文件的场景<br/>，可提升文件打开效率。<br/> |
| [setSandboxAppConfig](arkts-dataprotection-dlppermission-setsandboxappconfig-f.md#setSandboxAppConfig-1) | 设置沙箱应用配置信息，配置信息为JSON字符串格式，具体内容由应用自行设置。调用成功后，沙箱应用将按照配置信息运行。使用Promise异步回调。<br/><br/>该接口用于设置沙箱应用的配置信息，以便应用按需传递自定义参数。<br/> |
| [startDLPManagerForResult](arkts-dataprotection-dlppermission-startdlpmanagerforresult-f.md#startDLPManagerForResult-1) | 在当前[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-uiability-c.md#UIAbility)界面以无边框形式打开DLP权限管理应用。使用Promise异步回调。<br/><br/>该接口用于拉起DLP权限管理应用配置文件权限，并将用户操作结果返回给调用方。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口仅支持域账号调用。<br/> |
| <!--DelRow-->[uninstallDLPSandbox](arkts-dataprotection-dlppermission-uninstalldlpsandbox-f-sys.md#uninstallDLPSandbox-1) | 卸载一个应用的DLP沙箱。使用Promise异步回调。调用成功后，系统销毁指定的DLP沙箱环境并释放相关资源。<br/><br/>需要清理对应的沙箱环境时使用此接口。<br/><br/>必须在调用installDLPSandbox安装沙箱后才能调用此方法卸载。<br/> |
| <!--DelRow-->[uninstallDLPSandbox](arkts-dataprotection-dlppermission-uninstalldlpsandbox-f-sys.md#uninstallDLPSandbox-2) | 卸载一个应用的DLP沙箱。使用callback异步回调。调用成功后，系统销毁指定的DLP沙箱环境并释放相关资源。<br/><br/>需要清理沙箱环境时使用此接口。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [DlpConnManager](arkts-dataprotection-dlppermission-dlpconnmanager-c.md) | 用于调用registerPlugin和unregisterPlugin接口，在SA（System Ability）中注册或注销回调能力。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; registerPlugin接口将回调能力注册进SA（System Ability），而unregisterPlugin接口将回调能力从SA（System Ability）中注销。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessedDLPFileInfo](arkts-dataprotection-dlppermission-accesseddlpfileinfo-i.md) | 表示被打开的DLP文件的信息。<br/> |
| <!--DelRow-->[AuthUser](arkts-dataprotection-dlppermission-authuser-i-sys.md) | 表示授权用户数据。<br/> |
| [CustomProperty](arkts-dataprotection-dlppermission-customproperty-i.md) | 表示自定义策略。<br/> |
| <!--DelRow-->[CustomProperty](arkts-dataprotection-dlppermission-customproperty-i-sys.md) | 表示自定义策略。<br/> |
| <!--DelRow-->[DLPFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md) | 管理DLPFile的实例，表示一个DLP文件对象，需要通过<br/>[generateDLPFile](arkts-dataprotection-dlppermission-generatedlpfile-f-sys.md#generateDLPFile-1)<br/>/[openDLPFile](arkts-dataprotection-dlppermission-opendlpfile-f-sys.md#openDLPFile-1)获取DLPFile的实例。DLPFile对象代表一个已打开<br/>的DLP文件句柄，封装了对DLP文件的所有操作接口。对象在使用完毕后必须调用closeDLPFile方法释放资源，避免文件句柄泄漏。DLPFile对象在跨进程传递时，需要进行授权。<br/> |
| [DLPManagerResult](arkts-dataprotection-dlppermission-dlpmanagerresult-i.md) | 表示打开DLP权限管理应用的结果。<br/> |
| [DLPPermissionInfo](arkts-dataprotection-dlppermission-dlppermissioninfo-i.md) | 表示DLP文件的权限信息。<br/> |
| [DLPProperty](arkts-dataprotection-dlppermission-dlpproperty-i.md) | 表示授权相关信息。<br/> |
| <!--DelRow-->[DLPProperty](arkts-dataprotection-dlppermission-dlpproperty-i-sys.md) | 表示授权相关信息。<br/> |
| <!--DelRow-->[DLPSandboxInfo](arkts-dataprotection-dlppermission-dlpsandboxinfo-i-sys.md) | 表示DLP沙箱的信息。<br/> |
| <!--DelRow-->[DLPSandboxState](arkts-dataprotection-dlppermission-dlpsandboxstate-i-sys.md) | DLP沙箱的状态信息。<br/> |
| [DlpConnPlugin](arkts-dataprotection-dlppermission-dlpconnplugin-i.md) | 被用于registerPlugin接口中，将回调能力注册到SA（System Ability）中。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; [registerPlugin](arkts-dataprotection-dlppermission-dlpconnmanager-c.md#registerPlugin-1)接口的参数需要继承该接口，<br/>&gt; [connectServer](arkts-dataprotection-dlppermission-dlpconnplugin-i.md#connectServer-1)由SA（System Ability）侧调用，通过callback进行回传参数。<br/> |
| [DlpFileQueryOptions](arkts-dataprotection-dlppermission-dlpfilequeryoptions-i.md) | 表示企业DLP文件的查询选项。<br/> |
| [EnterprisePolicy](arkts-dataprotection-dlppermission-enterprisepolicy-i.md) | 表示企业定制策略。<br/> |
| [RetentionSandboxInfo](arkts-dataprotection-dlppermission-retentionsandboxinfo-i.md) | 保留沙箱的沙箱信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccountType](arkts-dataprotection-dlppermission-accounttype-e.md) | 表示授权账号类型的枚举。<br/> |
| <!--DelRow-->[AccountType](arkts-dataprotection-dlppermission-accounttype-e-sys.md) | 表示授权账号类型的枚举。<br/> |
| [ActionFlagType](arkts-dataprotection-dlppermission-actionflagtype-e.md) | 可以对DLP文件进行的操作类型枚举。例如：DLP沙箱应用可以根据是否具有操作权限，对其按钮进行置灰。<br/> |
| <!--DelRow-->[ActionType](arkts-dataprotection-dlppermission-actiontype-e-sys.md) | 表示在文件设定的权限时间到期后所执行的动作枚举，默认为NOT_OPEN。<br/> |
| [DLPFileAccess](arkts-dataprotection-dlppermission-dlpfileaccess-e.md) | DLP文件授权类型的枚举。<br/> |
| <!--DelRow-->[GatheringPolicyType](arkts-dataprotection-dlppermission-gatheringpolicytype-e-sys.md) | DLP沙箱聚合策略类型的枚举。沙箱聚合表示同一权限类型的DLP文件，在同一个沙箱内打开，例如在同一个沙箱内使用不同tab页打开；沙箱非聚合表示不同DLP文件在不同沙箱打开。<br/> |

