# @ohos.dlpPermission(数据防泄露)

数据防泄露（Data Loss Prevention，简称为DLP）是系统级的数据防泄露解决方案，提供跨设备文件的权限管理、加密存储、授权访问等能力。DLP通过加密技术对敏感文件进行保护，生成.dlp格式的加密文件（称为DLP文件）。当打开DLP文件时，系统会自动创建隔离的DLP沙箱环境，确保文件内容不会泄露到非授权环境。

> **说明：** 
> 
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - @ohos.dlpPermission归属的Kit已由`DataLossPreventionKit`变更为`DataProtectionKit`，建议开发者使用新模块名`@kit.DataProtectionKit`完成模块导入。如果使用`@kit.DataLossPreventionKit`导入，仅能调用改名前的接口，无法使用新增接口。

**起始版本：** 10

**系统能力：** SystemCapability.Security.DataLossPrevention

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancelRetentionState](arkts-dataprotection-dlppermission-cancelretentionstate-f.md#cancelretentionstate) | 取消沙箱保留状态，即恢复DLP文件关闭时自动卸载沙箱策略。使用Promise异步回调。 |
| [cancelRetentionState](arkts-dataprotection-dlppermission-cancelretentionstate-f.md#cancelretentionstate-1) | 取消沙箱保留状态即恢复DLP文件关闭时自动卸载沙箱策略。使用callback异步回调。 |
| [cleanSandboxAppConfig](arkts-dataprotection-dlppermission-cleansandboxappconfig-f.md) | 清理沙箱应用配置信息。调用成功后，沙箱应用配置将被清除，恢复默认状态。使用Promise异步回调。 |
| [closeOpenedEnterpriseDlpFiles](arkts-dataprotection-dlppermission-closeopenedenterprisedlpfiles-f.md) | 关闭当前打开的所有符合指定选项的企业DLP文件。使用Promise异步回调。 |
| [decryptDlpFile](arkts-dataprotection-dlppermission-decryptdlpfile-f.md) | 将DLP文件解密生成明文文件，仅支持企业账号调用。使用Promise异步回调。 |
| [generateDlpFileForEnterprise](arkts-dataprotection-dlppermission-generatedlpfileforenterprise-f.md) | 将明文文件加密生成企业账号DLP文件，仅支持企业账号调用。使用Promise异步回调。 |
| [getControlledAppLists](arkts-dataprotection-dlppermission-getcontrolledapplists-f.md) | 获取当前用户受企业DLP控制的应用程序列表。使用Promise异步回调。 |
| [getDLPFileAccessRecords](arkts-dataprotection-dlppermission-getdlpfileaccessrecords-f.md#getdlpfileaccessrecords) | 查询最近访问的DLP文件列表。调用成功后返回文件访问记录，用于追踪和管理DLP文件的使用情况。仅支持在非DLP沙箱应用中调用。使用Promise异步回调。 |
| [getDLPFileAccessRecords](arkts-dataprotection-dlppermission-getdlpfileaccessrecords-f.md#getdlpfileaccessrecords-1) | 查询最近访问的DLP文件列表。调用成功后返回文件访问记录，用于追踪和管理DLP文件的使用情况。仅支持在非DLP沙箱应用中调用。使用callback异步回调。 |
| [getDLPPermissionInfo](arkts-dataprotection-dlppermission-getdlppermissioninfo-f.md#getdlppermissioninfo) | 查询当前DLP沙箱的权限信息，包括文件授权类型及可执行操作（如查看、编辑、复制等）。仅支持在DLP沙箱应用中调用，使用Promise异步回调。 |
| [getDLPPermissionInfo](arkts-dataprotection-dlppermission-getdlppermissioninfo-f.md#getdlppermissioninfo-1) | 查询当前DLP沙箱的权限信息。返回的权限信息包括文件的授权类型和可执行的操作权限（如查看、编辑、复制等）。仅支持在DLP沙箱应用中调用。使用callback异步回调。 |
| [getDLPSuffix](arkts-dataprotection-dlppermission-getdlpsuffix-f.md) | 获取DLP文件扩展名。调用成功后返回DLP文件扩展名（如'.dlp'）。接口为同步接口。 |
| [getDLPSupportedFileTypes](arkts-dataprotection-dlppermission-getdlpsupportedfiletypes-f.md#getdlpsupportedfiletypes) | 查询当前可支持权限设置和校验的文件扩展名类型列表。调用成功后返回支持的文件类型列表，用于判断哪些文件类型可进行DLP权限管理。使用Promise异步回调。 |
| [getDLPSupportedFileTypes](arkts-dataprotection-dlppermission-getdlpsupportedfiletypes-f.md#getdlpsupportedfiletypes-1) | 查询当前可支持权限设置和校验的文件扩展名类型列表。调用成功后返回支持的文件类型列表，用于判断哪些文件类型可进行DLP权限管理。使用callback异步回调。 |
| [getOriginalFileName](arkts-dataprotection-dlppermission-getoriginalfilename-f.md) | 获取指定DLP文件名的原始文件名。该接口为同步接口。 |
| [getRetentionSandboxList](arkts-dataprotection-dlppermission-getretentionsandboxlist-f.md#getretentionsandboxlist) | 查询指定应用的保留沙箱信息列表。仅支持在非DLP沙箱应用中调用。使用Promise异步回调。 |
| [getRetentionSandboxList](arkts-dataprotection-dlppermission-getretentionsandboxlist-f.md#getretentionsandboxlist-1) | 查询指定应用的保留沙箱信息列表。仅支持在非DLP沙箱应用中调用。使用callback异步回调。 |
| [getRetentionSandboxList](arkts-dataprotection-dlppermission-getretentionsandboxlist-f.md#getretentionsandboxlist-2) | 查询当前应用的保留沙箱信息列表。使用callback异步回调。 |
| [getSandboxAppConfig](arkts-dataprotection-dlppermission-getsandboxappconfig-f.md) | 获取沙箱应用配置信息，使用Promise异步回调。 |
| [isDLPFeatureProvided](arkts-dataprotection-dlppermission-isdlpfeatureprovided-f.md) | 查询当前系统是否提供加密保护特性，仅支持企业设备且需[MDM（Mobile Device Management，移动设备管理）](../../../mdm/mdm-kit-intro.md)配置使能。调用成功后返回查询结果，用于判断系统是否支持DLP加密功能。使用Promise异步回调。 |
| [isDLPFile](arkts-dataprotection-dlppermission-isdlpfile-f.md#isdlpfile) | 根据文件的fd，查询该文件是否是DLP文件。使用Promise异步回调。 |
| [isDLPFile](arkts-dataprotection-dlppermission-isdlpfile-f.md#isdlpfile-1) | 根据文件的fd，查询该文件是否是DLP文件。调用成功后返回查询结果，true表示是DLP文件，false表示非DLP文件。使用callback异步回调。 |
| [isInSandbox](arkts-dataprotection-dlppermission-isinsandbox-f.md#isinsandbox) | 查询当前应用是否运行在DLP沙箱环境。使用Promise异步回调。 |
| [isInSandbox](arkts-dataprotection-dlppermission-isinsandbox-f.md#isinsandbox-1) | 查询当前应用是否运行在DLP沙箱环境。使用callback异步回调。 |
| [off](arkts-dataprotection-dlppermission-off-f.md#offopendlpfile) | 取消监听打开DLP文件。仅支持在非DLP沙箱应用中调用。调用成功后，将不再接收DLP文件打开事件的通知。 |
| [on](arkts-dataprotection-dlppermission-on-f.md#onopendlpfile) | 监听打开DLP文件。调用成功后，当DLP文件被打开时会触发回调通知当前应用。仅支持在非DLP沙箱应用中调用。 |
| [processPluginCommand](arkts-dataprotection-dlppermission-processplugincommand-f.md) | 处理透明加解密场景下的插件相关命令。使用Promise异步回调。 |
| [queryDlpPolicy](arkts-dataprotection-dlppermission-querydlppolicy-f.md) | 在DLP文件中解析文件头，获取DLP明文策略。返回的策略JSON字符串包含[DLPProperty](arkts-dataprotection-dlppermission-dlpproperty-i.md)和[CustomProperty](arkts-dataprotection-dlppermission-customproperty-i.md)信息。使用Promise异步回调。 |
| [queryOpenedEnterpriseDlpFiles](arkts-dataprotection-dlppermission-queryopenedenterprisedlpfiles-f.md) | 查询已打开且符合指定选项的企业DLP文件的URI列表。使用Promise异步回调。 |
| [setControlledAppLists](arkts-dataprotection-dlppermission-setcontrolledapplists-f.md) | 设置受企业DLP控制的应用程序列表。使用Promise异步回调。 |
| [setEnterprisePolicy](arkts-dataprotection-dlppermission-setenterprisepolicy-f.md) | 设置企业应用防护策略。调用成功后，企业应用的DLP防护将按照设置的策略执行。 |
| [setRetentionState](arkts-dataprotection-dlppermission-setretentionstate-f.md#setretentionstate) | 设置DLP沙箱的保留状态。默认情况下，打开DLP文件时系统会自动创建沙箱环境，关闭文件后自动销毁沙箱。设置保留状态后，即使关闭DLP文件，沙箱环境也会保留，便于快速重新打开相同DLP文件。适用于需要频繁操作同一DLP文件的场景，可提升文件打开效率。仅支持在DLP沙箱应用中调用。使用Promise异步回调。 |
| [setRetentionState](arkts-dataprotection-dlppermission-setretentionstate-f.md#setretentionstate-1) | 设置DLP沙箱的保留状态。默认情况下，打开DLP文件时系统会自动创建沙箱环境，关闭文件后自动销毁沙箱。设置保留状态后，即使关闭DLP文件，沙箱环境也会保留，便于快速重新打开相同DLP文件。适用于需要频繁操作同一DLP文件的场景，可提升文件打开效率。仅支持在DLP沙箱应用中调用。使用callback异步回调。 |
| [setSandboxAppConfig](arkts-dataprotection-dlppermission-setsandboxappconfig-f.md) | 设置沙箱应用配置信息，配置信息为JSON字符串格式，具体内容由应用自行设置。调用成功后，沙箱应用将按照配置信息运行。使用Promise异步回调。仅支持在非DLP沙箱应用中调用。 |
| [startDLPManagerForResult](arkts-dataprotection-dlppermission-startdlpmanagerforresult-f.md#startdlpmanagerforresult) | 在当前[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)界面以无边框形式打开DLP权限管理应用。使用Promise异步回调。 |
| [startDLPManagerForResult](arkts-dataprotection-dlppermission-startdlpmanagerforresult-f.md#startdlpmanagerforresult-1) | 在指定窗口内以无边框形式打开DLP权限管理应用。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [generateDLPFile](arkts-dataprotection-dlppermission-generatedlpfile-f-sys.md#generatedlpfile) | DLP管理应用调用该接口，将明文文件加密生成DLPFile管理对象，对象仅在授权列表内的用户可以打开，授权又分为完全控制权限和只读权限。使用Promise异步回调。 |
| [generateDLPFile](arkts-dataprotection-dlppermission-generatedlpfile-f-sys.md#generatedlpfile-1) | DLP管理应用调用该接口，将明文文件加密生成权限受控文件。仅授权列表内的用户可以打开该文件，授权又分为完全控制权限和只读权限。获取DLPFile管理对象，使用callback异步回调。使用完DLPFile对象后，应调用[closeDLPFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#closedlpfile)释放对象，避免资源泄漏。 |
| [getDLPGatheringPolicy](arkts-dataprotection-dlppermission-getdlpgatheringpolicy-f-sys.md#getdlpgatheringpolicy) | 查询DLP沙箱聚合策略。使用Promise异步回调。 |
| [getDLPGatheringPolicy](arkts-dataprotection-dlppermission-getdlpgatheringpolicy-f-sys.md#getdlpgatheringpolicy-1) | 查询DLP沙箱聚合策略。使用callback异步回调。 |
| [installDLPSandbox](arkts-dataprotection-dlppermission-installdlpsandbox-f-sys.md#installdlpsandbox) | 安装一个应用的DLP沙箱。DLP沙箱为受保护的DLP文件创建独立的运行环境，与原应用进程隔离，确保数据在授权范围内安全流转。沙箱应用继承原应用的功能但仅能访问授权的DLP文件。使用Promise异步回调。 |
| [installDLPSandbox](arkts-dataprotection-dlppermission-installdlpsandbox-f-sys.md#installdlpsandbox-1) | 安装一个应用的DLP沙箱。使用callback异步回调。调用成功后，系统为应用创建DLP沙箱环境并返回沙箱信息。 |
| [off](arkts-dataprotection-dlppermission-off-f-sys.md#offuninstalldlpsandbox) | 取消监听DLP沙箱卸载事件。调用成功后，应用不再接收DLP沙箱卸载事件的回调通知。 |
| [on](arkts-dataprotection-dlppermission-on-f-sys.md#onuninstalldlpsandbox) | 注册监听DLP沙箱卸载事件，用于感知沙箱环境的变化。注册成功后，当DLP沙箱被卸载时，系统会通过回调函数通知应用。 |
| [openDLPFile](arkts-dataprotection-dlppermission-opendlpfile-f-sys.md#opendlpfile) | DLP管理应用调用该接口，打开DLP文件。调用成功后返回DLPFile管理对象，可用于管理DLP文件的权限和进行相关操作。使用Promise异步回调。 |
| [openDLPFile](arkts-dataprotection-dlppermission-opendlpfile-f-sys.md#opendlpfile-1) | DLP管理应用调用该接口，打开DLP文件。使用callback异步回调。调用成功后返回DLPFile管理对象，可用于管理DLP文件的权限和进行相关操作。使用完DLPFile对象后，应调用closeDLPFile释放对象，避免资源泄漏。 |
| [uninstallDLPSandbox](arkts-dataprotection-dlppermission-uninstalldlpsandbox-f-sys.md#uninstalldlpsandbox) | 卸载一个应用的DLP沙箱。使用Promise异步回调。调用成功后，系统销毁指定的DLP沙箱环境并释放相关资源。 |
| [uninstallDLPSandbox](arkts-dataprotection-dlppermission-uninstalldlpsandbox-f-sys.md#uninstalldlpsandbox-1) | 卸载一个应用的DLP沙箱。使用callback异步回调。调用成功后，系统销毁指定的DLP沙箱环境并释放相关资源。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [DlpConnManager](arkts-dataprotection-dlppermission-dlpconnmanager-c.md) | 用于调用registerPlugin和unregisterPlugin接口，在SA（System Ability）中注册或注销回调能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessedDLPFileInfo](arkts-dataprotection-dlppermission-accesseddlpfileinfo-i.md) | 表示被打开的DLP文件的信息。 |
| [AuthUser](arkts-dataprotection-dlppermission-authuser-i.md) | 表示授权用户数据。 |
| [CustomProperty](arkts-dataprotection-dlppermission-customproperty-i.md) | 表示自定义策略。 |
| [DlpConnPlugin](arkts-dataprotection-dlppermission-dlpconnplugin-i.md) | 被用于registerPlugin接口中，将回调能力注册到SA（System Ability）中。 |
| [DlpFileQueryOptions](arkts-dataprotection-dlppermission-dlpfilequeryoptions-i.md) | 表示企业DLP文件的查询选项。 |
| [DLPManagerResult](arkts-dataprotection-dlppermission-dlpmanagerresult-i.md) | 表示打开DLP权限管理应用的结果。 |
| [DLPPermissionInfo](arkts-dataprotection-dlppermission-dlppermissioninfo-i.md) | 表示DLP文件的权限信息。 |
| [DLPProperty](arkts-dataprotection-dlppermission-dlpproperty-i.md) | 表示授权相关信息。 |
| [EnterprisePolicy](arkts-dataprotection-dlppermission-enterprisepolicy-i.md) | 表示企业定制策略。 |
| [RetentionSandboxInfo](arkts-dataprotection-dlppermission-retentionsandboxinfo-i.md) | 保留沙箱的沙箱信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DLPFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md) | 管理DLPFile的实例，表示一个DLP文件对象，需要通过[generateDLPFile](arkts-dataprotection-dlppermission-generatedlpfile-f-sys.md) /[openDLPFile](arkts-dataprotection-dlppermission-opendlpfile-f-sys.md)获取DLPFile的实例。DLPFile对象代表一个已打开的DLP文件句柄，封装了对DLP文件的所有操作接口。对象在使用完毕后必须调用[closeDLPFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#closedlpfile)方法释放资源，避免文件句柄泄漏。DLPFile对象在跨进程传递时，需要进行授权。 |
| [DLPSandboxInfo](arkts-dataprotection-dlppermission-dlpsandboxinfo-i-sys.md) | 表示DLP沙箱的信息。 |
| [DLPSandboxState](arkts-dataprotection-dlppermission-dlpsandboxstate-i-sys.md) | DLP沙箱的状态信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccountType](arkts-dataprotection-dlppermission-accounttype-e.md) | 表示授权账号类型的枚举。 |
| [ActionFlagType](arkts-dataprotection-dlppermission-actionflagtype-e.md) | 可以对DLP文件进行的操作类型枚举。例如：DLP沙箱应用可以根据是否具有操作权限，对其按钮进行置灰。 |
| [ActionType](arkts-dataprotection-dlppermission-actiontype-e.md) | 表示在文件设定的权限时间到期后所执行的动作枚举，默认为NOT_OPEN。 |
| [DLPFileAccess](arkts-dataprotection-dlppermission-dlpfileaccess-e.md) | DLP文件授权类型的枚举。 |
| [PluginCmd](arkts-dataprotection-dlppermission-plugincmd-e.md) | 可以执行的插件命令枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [GatheringPolicyType](arkts-dataprotection-dlppermission-gatheringpolicytype-e-sys.md) | DLP沙箱聚合策略类型的枚举。沙箱聚合表示同一权限类型的DLP文件，在同一个沙箱内打开，例如在同一个沙箱内使用不同tab页打开；沙箱非聚合表示不同DLP文件在不同沙箱打开。 |
<!--DelEnd-->
