# @ohos.update

**起始版本：** 9

<!--Device-unnamed-declare namespace update--><!--Device-unnamed-declare namespace update-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getLocalUpdater](arkts-basicservices-update-getlocalupdater-f-sys.md#getlocalupdater) | 获取本地升级对象，用于从本地存储设备（如SD卡）执行系统升级。调用此方法后，系统返回LocalUpdater工具类对象，提供本地升级包校验、安装等功能。  典型流程为：开发者准备升级包（格式为.zip或.bin）和证书文件（格式为.cert或.der） → 系统校验包签名和完整性 → 系统安装升级包 → 系统重启以应用新版本。  **原理说明**：  该方法获取本地升级工具对象，封装了升级包校验（验证数字签名、文件完整性、版本兼容性）和安装（解压写入系统分区）等功能。本地升级不依赖网络，从设备本地存储读取升级包。  **约束和限制**：  - 升级包必须从设备厂商官网或官方渠道下载，确保来源可信。  - 安装前必须先校验升级包（调用verifyUpgradePackage），未校验的包可能导致系统损坏。  - 升级过程中设备会重启，应用需做好状态保存。  - 调用getLocalUpdater相关接口时，需要权限ohos.permission.UPDATE_SYSTEM。  - 升级包文件路径长度不超过255字符。超出255字符时将抛出异常。 |
| [getOnlineUpdater](arkts-basicservices-update-getonlineupdater-f-sys.md#getonlineupdater) | 获取在线升级对象，可用于在线检查新版本、下载升级包、安装升级包等操作。适用于设备厂商的OTA(详见[术语](docroot://basic-services/update/update-kit-term.md))升级客户端应用、在线系统升级等场景，帮助用户及时获取系统更新，提升升级效率和用户体验。  **原理说明**：  该方法通过系统服务接口获取在线升级对象，该对象提供检查新版本、下载升级包、安装升级包等核心功能。  **约束和限制**：  - 检查新版本和下载升级包都必须依赖设备厂商部署的升级包管理服务器。 |
| [getRestorer](arkts-basicservices-update-getrestorer-f-sys.md#getrestorer) | 获取恢复出厂设置对象，用于执行恢复出厂设置相关操作。调用此方法后，系统返回Restorer工具类对象，提供三种恢复出厂方式：  - factoryReset（普通恢复出厂，用于清除用户数据分区。详见[术语](docroot://basic-services/update/update-kit-term.md)）。  - forceFactoryReset（强制恢复出厂，用于清除用户数据分区并同步清除文件密钥。详见[术语](docroot://basic-services/update/update-kit-term.md)）。  - deepFactoryReset（深度恢复出厂，用于通过scope参数指定清除范围：DATA仅清除用户数据分区，DATA_AND_OS同时清除用户数据和操作系统分区。详见[术语](docroot://basic-services/update/update-kit-term.md)）。  获取对象后可调用相应方法执行恢复出厂操作，设备将重启恢复到出厂初始状态。  **原理说明**：  该方法通过系统服务接口获取恢复出厂设置对象，封装了数据分区清除、密钥清除、系统分区清理等核心功能。  **约束和限制**：  - 恢复出厂操作不可逆，将永久删除用户数据，需提前提醒用户备份重要数据。  - 调用factoryReset，deepFactoryReset和getDeepFactoryResetInfo接口时，需要权限ohos.permission.FACTORY_RESET。  - 调用forceFactoryReset接口时，需要权限ohos.permission.FORCE_FACTORY_RESET。  - 操作过程中设备会自动重启，应用需做好状态保存。  - 深度恢复出厂(deepFactoryReset)耗时较长（根据设备存储容量，可能需要1-4小时），必须确保设备电量充足(建议电量>50%)。  - 建议在用户通过对话框或界面点击确认按钮后，再执行恢复出厂操作。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BusinessType](arkts-basicservices-update-businesstype-i-sys.md) | 升级业务类型。 |
| [CheckResult](arkts-basicservices-update-checkresult-i-sys.md) | 版本检查结果。 |
| [ClearOptions](arkts-basicservices-update-clearoptions-i-sys.md) | 清除异常选项，用于指定要清除的异常状态类型。 |
| [ComponentDescription](arkts-basicservices-update-componentdescription-i-sys.md) | 组件描述文件。 |
| [CurrentVersionInfo](arkts-basicservices-update-currentversioninfo-i-sys.md) | 当前版本信息。 |
| [DescriptionInfo](arkts-basicservices-update-descriptioninfo-i-sys.md) | 版本描述文件信息。 |
| [DescriptionOptions](arkts-basicservices-update-descriptionoptions-i-sys.md) | 描述文件选项，用于指定描述文件的格式和语言。对象包含format(描述文件格式，可选STANDARD或SIMPLIFIED)和language(语言代码，如'zh-cn')字段。 |
| [DownloadOptions](arkts-basicservices-update-downloadoptions-i-sys.md) | 下载选项，包含allowNetwork(允许下载的网络类型)和order(升级指令)字段，用于控制下载行为。 |
| [ErrorMessage](arkts-basicservices-update-errormessage-i-sys.md) | 错误信息。 |
| [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | 事件信息。 |
| [EventInfo](arkts-basicservices-update-eventinfo-i-sys.md) | 事件信息对象，用于接收升级事件通知时传递的事件详情。包含eventId(事件ID，标识具体事件类型)和taskBody(任务数据，包含任务状态和进度)字段。  使用场景：在注册事件监听(on方法)后，事件发生时回调函数会接收到EventInfo对象，通过解析eventId和taskBody可获知升级任务的实时状态和进度，用于实时监控升级流程。 |
| [FactoryResetInfo](arkts-basicservices-update-factoryresetinfo-i-sys.md) | 恢复出厂设置信息。 |
| [FactoryResetStrategy](arkts-basicservices-update-factoryresetstrategy-i-sys.md) | 恢复出厂设置策略，包含scope(重置范围)和strategy(重置策略描述)字段。 |
| [LocalUpdater](arkts-basicservices-update-localupdater-i-sys.md) | 提供校验本地升级包签名和完整性、安装本地升级包、监听本地升级事件等本地固件更新功能的工具类。  使用场景：离线环境系统升级、网络不稳定场景升级、自主可控升级流程。  **收益说明**：  解决无法联网自动升级的问题，适合离线环境或网络不稳定场景，无需依赖升级包管理服务器，降低升级成本，自主可控升级时间，确保系统完整性。  **实现机制**：  - 校验机制：验证升级包是否为官方发布且未被篡改，检查签名、完整性和版本兼容性。  - 安装机制：解压并写入升级包内容到系统分区，准备重启应用新版本。  - 安全保证：必须先校验升级包，确保来源可信后方可安装。 |
| [NewVersionInfo](arkts-basicservices-update-newversioninfo-i-sys.md) | 新版本数据。 |
| [PauseDownloadOptions](arkts-basicservices-update-pausedownloadoptions-i-sys.md) | 暂停下载选项，用于控制暂停行为。对象包含isAllowAutoResume字段，true表示允许自动恢复，false表示需手动恢复。 |
| [Restorer](arkts-basicservices-update-restorer-i-sys.md) | 提供清除用户数据分区、深度清除用户数据和操作系统分区、同步清除文件密钥等恢复出厂设置功能的工具类。  > **恢复出厂设置流程**：  - 开发者调用getRestorer方法获取Restorer对象。  - 开发者根据需求选择恢复出厂方式：1. factoryReset：普通恢复出厂，仅清除用户数据分区。2. forceFactoryReset：强制恢复出厂，清除用户数据分区并同步清除文件密钥。3. deepFactoryReset：深度恢复出厂，可通过scope参数指定清除范围：DATA仅清除用户数据分区，DATA_AND_OS同时清除用户数据和操作系统分区。  - 开发者调用相应的恢复出厂方法执行恢复出厂操作，设备将清除数据并恢复到出厂状态。  选取建议：日常维护场景优先选择factoryReset；涉及敏感数据或设备交接场景选择forceFactoryReset；设备报废或需要物理销毁数据场景选择deepFactoryReset。  **收益说明**：  帮助用户快速解决系统异常、释放存储空间、保护隐私数据，支持设备交接和安全销毁场景，满足不同安全级别的数据清除需求。 |
| [ResumeDownloadOptions](arkts-basicservices-update-resumedownloadoptions-i-sys.md) | 恢复下载选项，用于指定恢复下载的网络类型。对象包含allowNetwork字段，用于设置允许下载的网络类型。 |
| [TaskBody](arkts-basicservices-update-taskbody-i-sys.md) | 任务数据。 |
| [TaskInfo](arkts-basicservices-update-taskinfo-i-sys.md) | 任务信息。 |
| [Updater](arkts-basicservices-update-updater-i-sys.md) | 提供在线检查新版本、下载升级包、安装升级包、管理升级策略、获取版本信息等系统在线更新功能的工具类。  使用场景：设备厂商OTA升级客户端应用、在线系统升级、自动版本检查和升级管理。  **收益说明**：  支持用户及时获取系统更新，提升升级效率和用户体验，降低用户操作成本，支持自动版本检查、后台下载、断点续传等功能。  **实现机制**：  - 版本检查：向升级包管理服务器查询新版本信息。  - 下载管理：支持网络类型选择、暂停/恢复下载、断点续传。  - 安装机制：升级包下载完成后解压并写入系统分区，准备重启应用。  - 状态管理：维护升级任务状态，支持查询任务信息、清除异常状态、终止升级。 |
| [UpgradeFile](arkts-basicservices-update-upgradefile-i-sys.md) | 升级文件，包含文件类型和文件路径，用于指定要安装的本地升级包。 |
| [UpgradeInfo](arkts-basicservices-update-upgradeinfo-i-sys.md) | 升级信息。 |
| [UpgradeOptions](arkts-basicservices-update-upgradeoptions-i-sys.md) | 升级选项，包含升级指令等配置，用于指定升级操作类型。 |
| [UpgradePeriod](arkts-basicservices-update-upgradeperiod-i-sys.md) | 升级时间段。 |
| [UpgradePolicy](arkts-basicservices-update-upgradepolicy-i-sys.md) | 升级策略，用于控制升级行为。 |
| [VersionComponent](arkts-basicservices-update-versioncomponent-i-sys.md) | 版本组件。 |
| [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 版本摘要。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BusinessSubType](arkts-basicservices-update-businesssubtype-e-sys.md) | 升级类型。 |
| [BusinessVendor](arkts-basicservices-update-businessvendor-e-sys.md) | 设备厂家。 |
| [ComponentType](arkts-basicservices-update-componenttype-e-sys.md) | 组件类型。 |
| [DescriptionFormat](arkts-basicservices-update-descriptionformat-e-sys.md) | 描述文件格式。 |
| [DescriptionType](arkts-basicservices-update-descriptiontype-e-sys.md) | 描述文件类型。 |
| [EffectiveMode](arkts-basicservices-update-effectivemode-e-sys.md) | 生效模式。 |
| [EventClassify](arkts-basicservices-update-eventclassify-e-sys.md) | 事件类型。 |
| [EventId](arkts-basicservices-update-eventid-e-sys.md) | 事件ID。 |
| [FactoryResetScope](arkts-basicservices-update-factoryresetscope-e-sys.md) | 恢复出厂设置范围。 |
| [NetType](arkts-basicservices-update-nettype-e-sys.md) | 网络类型，用于指定下载的网络类型。设置CELLULAR仅允许数据网络下载，设置WIFI仅允许WIFI下载，设置CELLULAR_AND_WIFI允许两者均可下载。 |
| [Order](arkts-basicservices-update-order-e-sys.md) | 升级指令。 |
| [OtaMode](arkts-basicservices-update-otamode-e-sys.md) | 升级模式。 |
| [UpgradeAction](arkts-basicservices-update-upgradeaction-e-sys.md) | 升级方式。 |
| [UpgradeStatus](arkts-basicservices-update-upgradestatus-e-sys.md) | 升级状态。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | 事件回调。  **版本说明**： 从API version 23开始支持。 |
<!--DelEnd-->

