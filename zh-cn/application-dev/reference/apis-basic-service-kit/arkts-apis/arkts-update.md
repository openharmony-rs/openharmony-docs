# @ohos.update

升级范围：升级整个系统，包括内置资源和预置应用，不包括三方应用。

升级类型：SD卡升级、在线升级、恢复出厂升级。

- SD卡升级依赖升级包和SD卡安装。  
- 在线升级依赖设备厂商部署的用于管理升级包的服务器。服务器由设备厂商部署，IP由调用者传入，请求的request接口是固定的，由设备厂商开发。  
- 恢复出厂升级对象提供恢复出厂相关接口。

> **说明：**  
>  
> 本模块接口为系统接口。

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
| [getLocalUpdater](arkts-basicservices-update-getlocalupdater-f-sys.md#getlocalupdater-1) | 获取本地升级对象。 |
| [getOnlineUpdater](arkts-basicservices-update-getonlineupdater-f-sys.md#getonlineupdater-1) | 获取在线升级对象。 |
| [getRestorer](arkts-basicservices-update-getrestorer-f-sys.md#getrestorer-1) | 获取恢复出厂设置对象。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BusinessType](arkts-basicservices-update-businesstype-i-sys.md) | 升级业务类型。 |
| [CheckResult](arkts-basicservices-update-checkresult-i-sys.md) | 搜包结果。 |
| [ClearOptions](arkts-basicservices-update-clearoptions-i-sys.md) | 清除异常选项。 |
| [ComponentDescription](arkts-basicservices-update-componentdescription-i-sys.md) | 组件描述文件。 |
| [CurrentVersionInfo](arkts-basicservices-update-currentversioninfo-i-sys.md) | 当前版本信息。 |
| [DescriptionInfo](arkts-basicservices-update-descriptioninfo-i-sys.md) | 版本描述文件信息。 |
| [DescriptionOptions](arkts-basicservices-update-descriptionoptions-i-sys.md) | 描述文件选项。 |
| [DownloadOptions](arkts-basicservices-update-downloadoptions-i-sys.md) | 下载选项。 |
| [ErrorMessage](arkts-basicservices-update-errormessage-i-sys.md) | 错误信息。 |
| [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | 事件信息。 |
| [EventInfo](arkts-basicservices-update-eventinfo-i-sys.md) | 事件信息。 |
| [FactoryResetInfo](arkts-basicservices-update-factoryresetinfo-i-sys.md) | 恢复出厂设置信息。 |
| [FactoryResetStrategy](arkts-basicservices-update-factoryresetstrategy-i-sys.md) | 恢复出厂设置策略。 |
| [LocalUpdater](arkts-basicservices-update-localupdater-i-sys.md) | 提供本地固件更新功能的工具类。 |
| [NewVersionInfo](arkts-basicservices-update-newversioninfo-i-sys.md) | 新版本数据。 |
| [PauseDownloadOptions](arkts-basicservices-update-pausedownloadoptions-i-sys.md) | 暂停下载选项。 |
| [Restorer](arkts-basicservices-update-restorer-i-sys.md) | 提供设备恢复出厂设置功能的工具类。 |
| [ResumeDownloadOptions](arkts-basicservices-update-resumedownloadoptions-i-sys.md) | 恢复下载选项。 |
| [TaskBody](arkts-basicservices-update-taskbody-i-sys.md) | 任务数据。 |
| [TaskInfo](arkts-basicservices-update-taskinfo-i-sys.md) | 任务信息。 |
| [Updater](arkts-basicservices-update-updater-i-sys.md) | 提供系统在线更新功能的工具类。 |
| [UpgradeFile](arkts-basicservices-update-upgradefile-i-sys.md) | 升级文件。 |
| [UpgradeInfo](arkts-basicservices-update-upgradeinfo-i-sys.md) | 升级信息。 |
| [UpgradeOptions](arkts-basicservices-update-upgradeoptions-i-sys.md) | 升级选项。 |
| [UpgradePeriod](arkts-basicservices-update-upgradeperiod-i-sys.md) | 升级时间段。 |
| [UpgradePolicy](arkts-basicservices-update-upgradepolicy-i-sys.md) | 升级策略。 |
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
| [NetType](arkts-basicservices-update-nettype-e-sys.md) | 网络类型。 |
| [Order](arkts-basicservices-update-order-e-sys.md) | 升级指令。 |
| [OtaMode](arkts-basicservices-update-otamode-e-sys.md) | 升级模式。 |
| [UpgradeAction](arkts-basicservices-update-upgradeaction-e-sys.md) | 升级方式。 |
| [UpgradeStatus](arkts-basicservices-update-upgradestatus-e-sys.md) | 升级状态。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | 事件回调。 |
<!--DelEnd-->

