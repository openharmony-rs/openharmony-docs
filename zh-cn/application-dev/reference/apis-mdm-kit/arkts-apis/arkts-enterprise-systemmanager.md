# @ohos.enterprise.systemManager

本模块提供系统管理能力。
> **说明**：  
>  
> 本模块接口仅可在Stage模型下使用。  
>  
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 12

<!--Device-unnamed-declare namespace systemManager--><!--Device-unnamed-declare namespace systemManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addDisallowedNearLinkProtocols](arkts-mdm-systemmanager-adddisallowednearlinkprotocols-f.md#adddisallowednearlinkprotocols) | 为指定用户添加禁用的星闪协议名单。NearLink Kit（星闪服务）提供一种低功耗、高速率的短距离通信服务，支持星闪设备之间的连接、数据交互。<!--RP3--><!--RP3End-->本接口对键盘、手写笔等系统服务和系统应用不生效。 |
| [addKeyEventPolicies](arkts-mdm-systemmanager-addkeyeventpolicies-f.md#addkeyeventpolicies) | 添加按键事件处理策略。系统触发按键事件时，若匹配下发的按键事件策略，将通过[EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onkeyevent)回调通知MDM应用，并携带匹配策略的按键事件信息。 |
| [finishLogCollected](arkts-mdm-systemmanager-finishlogcollected-f.md#finishlogcollected) | 删除本MDM应用在当前用户下收集到的设备日志。 |
| [getAutoUnlockAfterReboot](arkts-mdm-systemmanager-getautounlockafterreboot-f.md#getautounlockafterreboot) | 获取设备是否重启自动解锁。 |
| [getDisallowedNearLinkProtocols](arkts-mdm-systemmanager-getdisallowednearlinkprotocols-f.md#getdisallowednearlinkprotocols) | 获取指定用户下禁用的星闪协议名单。 |
| [getInstallLocalEnterpriseAppEnabled](arkts-mdm-systemmanager-getinstalllocalenterpriseappenabled-f.md#getinstalllocalenterpriseappenabled) | 查询是否支持本地安装企业应用。 |
| [getInstallLocalEnterpriseAppEnabledForAccount](arkts-mdm-systemmanager-getinstalllocalenterpriseappenabledforaccount-f.md#getinstalllocalenterpriseappenabledforaccount) | 查询指定用户是否支持本地安装企业应用。 |
| [getKeyEventPolicies](arkts-mdm-systemmanager-getkeyeventpolicies-f.md#getkeyeventpolicies) | 获取按键事件处理策略。 |
| [getNTPServer](arkts-mdm-systemmanager-getntpserver-f.md#getntpserver) | 获取NTP时间服务器信息。 |
| [getOtaUpdatePolicy](arkts-mdm-systemmanager-getotaupdatepolicy-f.md#getotaupdatepolicy) | 查询升级策略。 |
| [getUpdateAuthData](arkts-mdm-systemmanager-getupdateauthdata-f.md#getupdateauthdata) | 获取系统更新的鉴权数据，用于校验系统更新信息。使用Promise异步回调。 |
| [getUpdateResult](arkts-mdm-systemmanager-getupdateresult-f.md#getupdateresult) | 获取系统更新结果。使用Promise异步回调。 |
| [isActivationLockDisabled](arkts-mdm-systemmanager-isactivationlockdisabled-f.md#isactivationlockdisabled) | 获取设备激活锁禁用状态。 |
| [isOtaUpdateNonceEnable](arkts-mdm-systemmanager-isotaupdatenonceenable-f.md#isotaupdatenonceenable) | 查询是否使能服务器端生成随机Nonce标记 |
| [notifyUpdatePackages](arkts-mdm-systemmanager-notifyupdatepackages-f.md#notifyupdatepackages) | 通知系统更新包信息。内网升级场景下，需要先调用该接口通知系统更新包，再调用[systemManager.setOtaUpdatePolicy](arkts-mdm-systemmanager-setotaupdatepolicy-f.md#setotaupdatepolicy)设置升级策略。使用Promise异步回调。 |
| [removeDisallowedNearLinkProtocols](arkts-mdm-systemmanager-removedisallowednearlinkprotocols-f.md#removedisallowednearlinkprotocols) | 为指定用户移除禁用的星闪协议名单。 |
| [removeKeyEventPolicies](arkts-mdm-systemmanager-removekeyeventpolicies-f.md#removekeyeventpolicies) | 删除按键事件处理策略。 |
| [setActivationLockDisabled](arkts-mdm-systemmanager-setactivationlockdisabled-f.md#setactivationlockdisabled) | 禁用/启用设备激活锁。设备激活锁被禁用后，将无法使用查找设备功能。该功能只适用于特定设备<!--RP5--><!--RP5End-->。 |
| [setAutoUnlockAfterReboot](arkts-mdm-systemmanager-setautounlockafterreboot-f.md#setautounlockafterreboot) | 设置设备重启自动解锁，仅针对无锁屏密码设备生效。 |
| [setInstallLocalEnterpriseAppEnabled](arkts-mdm-systemmanager-setinstalllocalenterpriseappenabled-f.md#setinstalllocalenterpriseappenabled) | 设置是否支持本地安装企业应用。设置为支持安装后，具备本地安装能力的PC/2in1企业设备可本地双击应用安装包，安装签名证书分发类型为enterprise_normal的企业应用。 |
| [setInstallLocalEnterpriseAppEnabledForAccount](arkts-mdm-systemmanager-setinstalllocalenterpriseappenabledforaccount-f.md#setinstalllocalenterpriseappenabledforaccount) | 设置指定用户下是否支持本地安装企业应用。在具备本地安装能力的PC/2in1企业设备上下发支持本地企业应用策略后，用户可以在桌面或者文件管理器直接双击企业应用安装包，即可直接安装企业应用。  仅支持enterprise_normal或enterprise_mdm签名类型的企业应用。 |
| [setNTPServer](arkts-mdm-systemmanager-setntpserver-f.md#setntpserver) | 设置NTP(Network Time Protocol)时间服务器。 |
| [setOtaUpdateNonceEnable](arkts-mdm-systemmanager-setotaupdatenonceenable-f.md#setotaupdatenonceenable) | 使能服务器端生成随机Nonce标记 |
| [setOtaUpdatePolicy](arkts-mdm-systemmanager-setotaupdatepolicy-f.md#setotaupdatepolicy) | 设置升级策略。内网升级场景下，需要先调用[systemManager.notifyUpdatePackages](arkts-mdm-systemmanager-notifyupdatepackages-f.md#notifyupdatepackages)接口通知系统更新包，再调用该接口设置升级策略。 |
| [startCollectLog](arkts-mdm-systemmanager-startcollectlog-f.md#startcollectlog) | 开始收集设备上已生成并存储至硬盘的[faultlog](../../apis-performance-analysis-kit/arkts-apis/arkts-performanceanalysis-faultlogger-faulttype-e.md)日志，不支持收集未存储至硬盘的faultlog日志、应用业务日志和系统运行日志。  - 调用接口后，系统会启动一个日志收集任务，任务启动后接口立即返回。任务可能会因为系统性能等原因导致收集失败。  - 允许多个MDM应用调用，不同MDM应用在不同用户下收集的日志分开保存，互不影响。同一时间只允许一个MDM应用启动日志收集任务，在任务执行完成前调用本接口会返回错误码9201009，任务执行完成后，允许其他MDM应用调用。  - 任务执行完成后，通过[EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onlogcollected)回调函数通知给MDM应用，系统将已收集的日志文件挂载到MDM应用沙箱路径，MDM应用可以在回调函数中读取已收集的日志。  - 如果日志收集任务执行超过5分钟，[EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onlogcollected)回调函数会返回日志收集任务失败。  - 应用取走日志后，建议调用[systemManager.finishLogCollected](arkts-mdm-systemmanager-finishlogcollected-f.md#finishlogcollected)删除已收集到的日志。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ErrorInfo](arkts-mdm-systemmanager-errorinfo-i.md) | 系统更新错误信息。 |
| [KeyEvent](arkts-mdm-systemmanager-keyevent-i.md) | 按键事件。[EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onkeyevent)按键事件回调触发时，传递当前按键事件信息。 |
| [KeyEventPolicy](arkts-mdm-systemmanager-keyeventpolicy-i.md) | 按键事件处理策略。按键事件发生时，仅拦截响应已下发按键事件处理策略的按键。对于未下发按键事件处理策略的按键事件，系统执行原先的响应逻辑。 |
| [KeyItem](arkts-mdm-systemmanager-keyitem-i.md) | 其他按键信息。当前[KeyCode](arkts-mdm-systemmanager-keycode-e.md)事件发生时，其他已被按下的按键信息。 |
| [NotifyDescription](arkts-mdm-systemmanager-notifydescription-i.md) | 企业自定义更新通知说明。 |
| [OtaUpdatePolicy](arkts-mdm-systemmanager-otaupdatepolicy-i.md) | 升级策略。 |
| [Package](arkts-mdm-systemmanager-package-i.md) | 系统更新包详情。 |
| [PackageDescription](arkts-mdm-systemmanager-packagedescription-i.md) | 系统更新包描述信息。 |
| [SystemUpdateInfo](arkts-mdm-systemmanager-systemupdateinfo-i.md) | 待更新的系统版本信息。 |
| [UpdatePackageInfo](arkts-mdm-systemmanager-updatepackageinfo-i.md) | 系统更新包信息。 |
| [UpdateResult](arkts-mdm-systemmanager-updateresult-i.md) | 系统更新结果信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [KeyAction](arkts-mdm-systemmanager-keyaction-e.md) | 按键动作。 |
| [KeyCode](arkts-mdm-systemmanager-keycode-e.md) | 按键编码。[添加按键事件策略](arkts-mdm-systemmanager-addkeyeventpolicies-f.md#addkeyeventpolicies)、[删除按键事件策略](arkts-mdm-systemmanager-removekeyeventpolicies-f.md#removekeyeventpolicies)、[获取按键事件策略](arkts-mdm-systemmanager-getkeyeventpolicies-f.md#getkeyeventpolicies)和[按键事件回调](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onkeyevent)接口通过按键编码映射到设备对应实际按键。 |
| [KeyPolicy](arkts-mdm-systemmanager-keypolicy-e.md) | 按键策略。MDM应用下发按键策略的按键编码与系统按键事件匹配后的系统行为。 |
| [NearLinkProtocol](arkts-mdm-systemmanager-nearlinkprotocol-e.md) | 星闪协议枚举。 |
| [PackageType](arkts-mdm-systemmanager-packagetype-e.md) | 系统更新包类型。 |
| [PolicyType](arkts-mdm-systemmanager-policytype-e.md) | 升级策略类型枚举。 |
| [UpdateStatus](arkts-mdm-systemmanager-updatestatus-e.md) | 系统更新状态。 |

