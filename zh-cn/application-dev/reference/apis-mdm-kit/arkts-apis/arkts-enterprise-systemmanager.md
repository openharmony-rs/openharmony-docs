# @ohos.enterprise.systemManager

本模块提供系统管理能力。

> **说明**：
>
> 本模块接口仅可在Stage模型下使用。
>
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../../mdm/mdm-kit-guide.md)。

**起始版本：** 12

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addDisallowedNearLinkProtocols](arkts-mdm-adddisallowednearlinkprotocols-f.md#adddisallowednearlinkprotocols-1) | 为指定用户添加禁用的星闪协议名单。NearLink Kit（星闪服务）提供一种低功耗、高速率的短距离通信服务，支持星闪设备之间的连接、数据交互。&lt;!--RP3--&gt;&lt;!--RP3End--&gt;本接口对键盘、手写笔等系统服务和系统应用不生效。 |
| [addKeyEventPolicies](arkts-mdm-addkeyeventpolicies-f.md#addkeyeventpolicies-1) | 添加按键事件处理策略。系统触发按键事件时，若匹配下发的按键事件策略，将通过[EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterpriseadminextensionability-c.md#onkeyevent-1)回调通知MDM应用，并携带匹配策略的按键事件信息。 |
| [finishLogCollected](arkts-mdm-finishlogcollected-f.md#finishlogcollected-1) | 删除本MDM应用在当前用户下收集到的设备日志。@link systemManager.startCollectLog}开始收集日志后，收到&gt; [EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterpriseadminextensionability-c.md#onlogcollected-1)&gt; 回调时，建议立即拷贝或者处理日志，并调用此接口删除收集到的日志。&gt;&gt; 若不调本接口，设备日志会占用系统存储空间，不影响下一次调用[startCollectLog](arkts-mdm-startcollectlog-f.md#startcollectlog-1)启动日志收集任务。 |
| [getAutoUnlockAfterReboot](arkts-mdm-getautounlockafterreboot-f.md#getautounlockafterreboot-1) | 获取设备是否重启自动解锁。 |
| [getDisallowedNearLinkProtocols](arkts-mdm-getdisallowednearlinkprotocols-f.md#getdisallowednearlinkprotocols-1) | 获取指定用户下禁用的星闪协议名单。 |
| [getInstallLocalEnterpriseAppEnabled](arkts-mdm-getinstalllocalenterpriseappenabled-f.md#getinstalllocalenterpriseappenabled-1) | 查询是否支持本地安装企业应用。 |
| [getInstallLocalEnterpriseAppEnabledForAccount](arkts-mdm-getinstalllocalenterpriseappenabledforaccount-f.md#getinstalllocalenterpriseappenabledforaccount-1) | 查询指定用户是否支持本地安装企业应用。 |
| [getKeyEventPolicies](arkts-mdm-getkeyeventpolicies-f.md#getkeyeventpolicies-1) | 获取按键事件处理策略。 |
| [getNTPServer](arkts-mdm-getntpserver-f.md#getntpserver-1) | 获取NTP时间服务器信息。 |
| [getOtaUpdatePolicy](arkts-mdm-getotaupdatepolicy-f.md#getotaupdatepolicy-1) | 查询升级策略。 |
| [getUpdateAuthData](arkts-mdm-getupdateauthdata-f.md#getupdateauthdata-1) | 获取系统更新的鉴权数据，用于校验系统更新信息。使用Promise异步回调。 |
| [getUpdateResult](arkts-mdm-getupdateresult-f.md#getupdateresult-1) | 获取系统更新结果。使用Promise异步回调。 |
| [isActivationLockDisabled](arkts-mdm-isactivationlockdisabled-f.md#isactivationlockdisabled-1) | 获取设备激活锁禁用状态。 |
| [isOtaUpdateNonceEnable](arkts-mdm-isotaupdatenonceenable-f.md#isotaupdatenonceenable-1) | 查询是否使能服务器端生成随机Nonce标记 |
| [notifyUpdatePackages](arkts-mdm-notifyupdatepackages-f.md#notifyupdatepackages-1) | 通知系统更新包信息。内网升级场景下，需要先调用该接口通知系统更新包，再调用[systemManager.setOtaUpdatePolicy](arkts-mdm-setotaupdatepolicy-f.md#setotaupdatepolicy-1)设置升级策略。使用Promise异步回调。 |
| [removeDisallowedNearLinkProtocols](arkts-mdm-removedisallowednearlinkprotocols-f.md#removedisallowednearlinkprotocols-1) | 为指定用户移除禁用的星闪协议名单。 |
| [removeKeyEventPolicies](arkts-mdm-removekeyeventpolicies-f.md#removekeyeventpolicies-1) | 删除按键事件处理策略。 |
| [setActivationLockDisabled](arkts-mdm-setactivationlockdisabled-f.md#setactivationlockdisabled-1) | 禁用/启用设备激活锁。设备激活锁被禁用后，将无法使用查找设备功能。该功能只适用于特定设备&lt;!--RP5--&gt;&lt;!--RP5End--&gt;。 |
| [setAutoUnlockAfterReboot](arkts-mdm-setautounlockafterreboot-f.md#setautounlockafterreboot-1) | 设置设备重启自动解锁，仅针对无锁屏密码设备生效。 |
| [setInstallLocalEnterpriseAppEnabled](arkts-mdm-setinstalllocalenterpriseappenabled-f.md#setinstalllocalenterpriseappenabled-1) | 设置是否支持本地安装企业应用。设置为支持安装后，具备本地安装能力的PC/2in1企业设备可本地双击应用安装包，安装签名证书分发类型为enterprise_normal的企业应用。 |
| [setInstallLocalEnterpriseAppEnabledForAccount](arkts-mdm-setinstalllocalenterpriseappenabledforaccount-f.md#setinstalllocalenterpriseappenabledforaccount-1) | 设置指定用户下是否支持本地安装企业应用。在具备本地安装能力的PC/2in1企业设备上下发支持本地企业应用策略后，用户可以在桌面或者文件管理器直接双击企业应用安装包，即可直接安装企业应用。仅支持enterprise_normal或enterprise_mdm签名类型的企业应用。 |
| [setNTPServer](arkts-mdm-setntpserver-f.md#setntpserver-1) | 设置NTP(Network Time Protocol)时间服务器。 |
| [setOtaUpdateNonceEnable](arkts-mdm-setotaupdatenonceenable-f.md#setotaupdatenonceenable-1) | 使能服务器端生成随机Nonce标记 |
| [setOtaUpdatePolicy](arkts-mdm-setotaupdatepolicy-f.md#setotaupdatepolicy-1) | 设置升级策略。内网升级场景下，需要先调用[systemManager.notifyUpdatePackages](arkts-mdm-notifyupdatepackages-f.md#notifyupdatepackages-1)接口通知系统更新包，再调用该接口设置升级策略。 |
| [startCollectLog](arkts-mdm-startcollectlog-f.md#startcollectlog-1) | 开始收集设备上已生成并存储至硬盘的[faultlog](@ohos.faultLogger:FaultLogger.FaultType)日志，不支持收集未存储至硬盘的faultlog日志、应用业务日志和系统运行日志。- 调用接口后，系统会启动一个日志收集任务，任务启动后接口立即返回。任务可能会因为系统性能等原因导致收集失败。- 允许多个MDM应用调用，不同MDM应用在不同用户下收集的日志分开保存，互不影响。同一时间只允许一个MDM应用启动日志收集任务，在任务执行完成前调用本接口会返回错误码9201009，任务执行完成后，允许其他MDM应用调用。- 任务执行完成后，通过[EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterpriseadminextensionability-c.md#onlogcollected-1)回调函数通知给MDM应用，系统将已收集的日志文件挂载到MDM应用沙箱路径，MDM应用可以在回调函数中读取已收集的日志。- 如果日志收集任务执行超过5分钟，[EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterpriseadminextensionability-c.md#onlogcollected-1)回调函数会返回日志收集任务失败。- 应用取走日志后，建议调用[systemManager.finishLogCollected](arkts-mdm-finishlogcollected-f.md#finishlogcollected-1)删除已收集到的日志。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ErrorInfo](arkts-mdm-errorinfo-i.md) | 系统更新错误信息。 |
| [KeyEvent](arkts-mdm-keyevent-i.md) | 按键事件。[EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterpriseadminextensionability-c.md#onkeyevent-1)按键事件回调触发时，传递当前按键事件信息。 |
| [KeyEventPolicy](arkts-mdm-keyeventpolicy-i.md) | 按键事件处理策略。按键事件发生时，仅拦截响应已下发按键事件处理策略的按键。对于未下发按键事件处理策略的按键事件，系统执行原先的响应逻辑。 |
| [KeyItem](arkts-mdm-keyitem-i.md) | 其他按键信息。当前[KeyCode](arkts-mdm-keycode-e.md)事件发生时，其他已被按下的按键信息。 |
| [NotifyDescription](arkts-mdm-notifydescription-i.md) | 企业自定义更新通知说明。 |
| [OtaUpdatePolicy](arkts-mdm-otaupdatepolicy-i.md) | 升级策略。 |
| [Package](arkts-mdm-package-i.md) | 系统更新包详情。 |
| [PackageDescription](arkts-mdm-packagedescription-i.md) | 系统更新包描述信息。 |
| [UpdatePackageInfo](arkts-mdm-updatepackageinfo-i.md) | 系统更新包信息。 |
| [UpdateResult](arkts-mdm-updateresult-i.md) | 系统更新结果信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SystemUpdateInfo](arkts-mdm-systemupdateinfo-i.md) | 待更新的系统版本信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [KeyAction](arkts-mdm-keyaction-e.md) | 按键动作。 |
| [KeyCode](arkts-mdm-keycode-e.md) | 按键编码。[添加按键事件策略](arkts-mdm-addkeyeventpolicies-f.md#addkeyeventpolicies-1)、[删除按键事件策略](arkts-mdm-removekeyeventpolicies-f.md#removekeyeventpolicies-1)、[获取按键事件策略](arkts-mdm-getkeyeventpolicies-f.md#getkeyeventpolicies-1)和[按键事件回调](arkts-mdm-enterpriseadminextensionability-c.md#onkeyevent-1)接口通过按键编码映射到设备对应实际按键。 |
| [KeyPolicy](arkts-mdm-keypolicy-e.md) | 按键策略。MDM应用下发按键策略的按键编码与系统按键事件匹配后的系统行为。 |
| [NearLinkProtocol](arkts-mdm-nearlinkprotocol-e.md) | 星闪协议枚举。 |
| [PackageType](arkts-mdm-packagetype-e.md) | 系统更新包类型。 |
| [PolicyType](arkts-mdm-policytype-e.md) | 升级策略类型枚举。 |
| [UpdateStatus](arkts-mdm-updatestatus-e.md) | 系统更新状态。 |

