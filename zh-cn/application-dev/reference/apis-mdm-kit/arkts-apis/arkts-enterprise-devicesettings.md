# @ohos.enterprise.deviceSettings

本模块提供企业设备设置能力，支持设置和获取设备息屏时间、系统时间、电源策略、护眼模式、默认输入法、壁纸、隐藏设置项等。 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

<!--Device-unnamed-declare namespace deviceSettings--><!--Device-unnamed-declare namespace deviceSettings-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addHiddenSettingsMenu](arkts-mdm-devicesettings-addhiddensettingsmenu-f.md) | 添加设置项至当前用户下的隐藏设置项列表。添加至隐藏设置项列表的设置项在当前用户的设置菜单中会被隐藏，隐藏后不可以在设置的搜索中搜索到。如果通过某种方式搜索到该设置项，点击后也无法打开。调用接口后即刻生效，无需重启设置应用。 |
| [getHiddenSettingsMenu](arkts-mdm-devicesettings-gethiddensettingsmenu-f.md) | 获取配置在当前用户下被隐藏的设置项列表。 |
| [getValue](arkts-mdm-devicesettings-getvalue-f.md) | 获取设备设置策略。 |
| [getValueForAccount](arkts-mdm-devicesettings-getvalueforaccount-f.md) | 获取指定用户的设备设置策略。该接口可以获取指定用户在设置应用中的某个参数，比如获取用户100的设备名称等。 |
| [removeHiddenSettingsMenu](arkts-mdm-devicesettings-removehiddensettingsmenu-f.md) | 将设置项从当前用户下的隐藏设置项列表中移除。隐藏设置项列表中的设置项在当前用户的设置菜单中会被隐藏，隐藏后不可以在设置的搜索中搜索到，如果通过某种方式搜索到该设置项，点击后也无法打开。若移除后剩余的隐藏设置项列表为空，则设置项会全 部显示。调用接口后即刻生效，无需重启设置应用。 从API版本26.0.0开始，调用 [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md)接口禁用 [SUPER_HUB](arkts-mdm-restrictions-featureforaccount-e.md)后，再调用该接口将中转站从隐藏设置项列表中移除时，会发生策略冲突，抛出9 200010错误码。 |
| [setHomeWallpaper](arkts-mdm-devicesettings-sethomewallpaper-f.md) | 设置桌面壁纸，使用Promise异步回调。 |
| [setSwitchStatus](arkts-mdm-devicesettings-setswitchstatus-f.md) | 设置开关的状态。支持设置星闪、蓝牙、Wi-Fi、NFC的状态为开启或关闭，设置完毕后，用户可以手动开关。支持设置蓝牙、NFC的状态为强制开启，设置完毕后，用户不可以手动开关。若已经通过 [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) 接口禁用了某个开关，则通过本接口设置这个开关的 状态会抛出错误码203，需通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) 接口解除该开关禁 用策略。当设备有多个MDM应用时，各MDM应用设置开关状态不存在冲突，最后设置的策略生效。开启(用户可手动开启、关闭)、关闭(用户可手动开启、关闭)、强制开启(用户不可手动关闭)三个状态可以随意切换，也不存在冲突。 |
| [setUnlockWallpaper](arkts-mdm-devicesettings-setunlockwallpaper-f.md) | 设置锁屏壁纸，使用Promise异步回调。企业设备管理应用可通过此接口统一设置企业设备的锁屏壁纸，用于企业形象展示或安全管控等场景。 |
| [setValue](arkts-mdm-devicesettings-setvalue-f.md) | 设置设备策略。 |
| [setValueForAccount](arkts-mdm-devicesettings-setvalueforaccount-f.md) | 设置指定用户的设备设置策略。该接口可以设置指定用户在设置应用中的某个参数，比如设置用户100的设备名称等。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getPowerPolicy](arkts-mdm-devicesettings-getpowerpolicy-f-sys.md) | 获取电源策略。 |
| [getScreenOffTime](arkts-mdm-devicesettings-getscreenofftime-f-sys.md) | 获取设备息屏时间，使用callback异步回调。 |
| [getScreenOffTime](arkts-mdm-devicesettings-getscreenofftime-f-sys.md) | 获取设备息屏时间，使用Promise异步回调。 |
| [installUserCertificate](arkts-mdm-devicesettings-installusercertificate-f-sys.md) | 安装用户证书，使用callback异步回调。 |
| [installUserCertificate](arkts-mdm-devicesettings-installusercertificate-f-sys.md) | 安装用户证书，使用Promise异步回调。 |
| [setPowerPolicy](arkts-mdm-devicesettings-setpowerpolicy-f-sys.md) | 设置电源策略。 |
| [setScreenOffTime](arkts-mdm-devicesettings-setscreenofftime-f-sys.md) | 设置设备息屏时间。 |
| [uninstallUserCertificate](arkts-mdm-devicesettings-uninstallusercertificate-f-sys.md) | 卸载用户证书，使用callback异步回调。 |
| [uninstallUserCertificate](arkts-mdm-devicesettings-uninstallusercertificate-f-sys.md) | 卸载用户证书，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CertBlob](arkts-mdm-devicesettings-certblob-i-sys.md) | 证书信息。 |
| [PowerPolicy](arkts-mdm-devicesettings-powerpolicy-i-sys.md) | 电源策略。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SettingsItem](arkts-mdm-devicesettings-settingsitem-e.md) | 设置的策略类型。 |
| [SettingsMenu](arkts-mdm-devicesettings-settingsmenu-e.md) | 设置项列表。 |
| [SwitchKey](arkts-mdm-devicesettings-switchkey-e.md) | 开关名称的枚举。 |
| [SwitchStatus](arkts-mdm-devicesettings-switchstatus-e.md) | 开关状态的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PowerPolicyAction](arkts-mdm-devicesettings-powerpolicyaction-e-sys.md) | 执行电源策略的动作。 |
| [PowerScene](arkts-mdm-devicesettings-powerscene-e-sys.md) | 执行电源策略的场景。 |
<!--DelEnd-->

