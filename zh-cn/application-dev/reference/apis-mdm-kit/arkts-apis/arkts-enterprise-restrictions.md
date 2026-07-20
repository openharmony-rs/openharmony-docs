# @ohos.enterprise.restrictions

本模块提供设置通用限制类策略能力。可以全局禁用和解除禁用蓝牙、HDC、USB、Wi-Fi等特性。

> **说明**：  
>  
> 本模块接口仅可在Stage模型下使用。  
>  
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](docroot://mdm/mdm-kit-guide.md)。

**起始版本：** 10

<!--Device-unnamed-declare namespace restrictions--><!--Device-unnamed-declare namespace restrictions-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { restrictions } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addDisallowedListForAccount](arkts-mdm-restrictions-adddisallowedlistforaccount-f.md#adddisallowedlistforaccount) | 为指定用户添加禁止使用某特性的应用名单。指定用户下，添加到名单中的应用不允许使用指定的特性能力。 |
| [getDisallowedListForAccount](arkts-mdm-restrictions-getdisallowedlistforaccount-f.md#getdisallowedlistforaccount) | 获取指定用户禁止使用某特性的应用名单。 |
| [getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy) | 查询某特性是否被禁用。 |
| [getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1) | 查询指定设备特性是否被禁用。 |
| [getDisallowedPolicyForAccount](arkts-mdm-restrictions-getdisallowedpolicyforaccount-f.md#getdisallowedpolicyforaccount) | 获取指定用户的某特性状态。 |
| [getDisallowedPolicyForAccount](arkts-mdm-restrictions-getdisallowedpolicyforaccount-f.md#getdisallowedpolicyforaccount-1) | 获取指定用户的某特性状态。 |
| [getUserRestricted](arkts-mdm-restrictions-getuserrestricted-f.md#getuserrestricted) | 获取设置项的禁用状态。 |
| [getUserRestrictedForAccount](arkts-mdm-restrictions-getuserrestrictedforaccount-f.md#getuserrestrictedforaccount) | 获取指定用户设置项的禁用状态。 |
| [removeDisallowedListForAccount](arkts-mdm-restrictions-removedisallowedlistforaccount-f.md#removedisallowedlistforaccount) | 为指定用户移除禁止使用某特性的应用名单。 |
| [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy) | 设置禁用/启用某特性。 |
| [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1) | 设置禁用/启用指定设备特性，禁用后相关设备特性无法被使用。 |
| [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setdisallowedpolicyforaccount) | 设置禁用/启用指定用户的某特性。 |
| [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setdisallowedpolicyforaccount-1) | 设置禁用/启用指定用户的某特性。 |
| [setUserRestriction](arkts-mdm-restrictions-setuserrestriction-f.md#setuserrestriction) | 设置用户行为的限制规则。 |
| [setUserRestrictionForAccount](arkts-mdm-restrictions-setuserrestrictionforaccount-f.md#setuserrestrictionforaccount) | 设置指定用户行为的限制规则。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disableMicrophone](arkts-mdm-restrictions-disablemicrophone-f-sys.md#disablemicrophone) | 使设备禁用或启用麦克风。 |
| [isFingerprintAuthDisabled](arkts-mdm-restrictions-isfingerprintauthdisabled-f-sys.md#isfingerprintauthdisabled) | 查询指纹认证是否被禁用。 |
| [isHdcDisabled](arkts-mdm-restrictions-ishdcdisabled-f-sys.md#ishdcdisabled) | 查询HDC是否被禁用。使用callback异步回调。 |
| [isHdcDisabled](arkts-mdm-restrictions-ishdcdisabled-f-sys.md#ishdcdisabled-1) | 查询HDC是否被禁用。使用Promise异步回调。 |
| [isMicrophoneDisabled](arkts-mdm-restrictions-ismicrophonedisabled-f-sys.md#ismicrophonedisabled) | 查询麦克风是否被禁用。 |
| [isPrinterDisabled](arkts-mdm-restrictions-isprinterdisabled-f-sys.md#isprinterdisabled) | 查询设备打印能力是否被禁用。使用callback异步回调。 |
| [isPrinterDisabled](arkts-mdm-restrictions-isprinterdisabled-f-sys.md#isprinterdisabled-1) | 查询设备打印能力是否被禁用。使用Promise异步回调。 |
| [setFingerprintAuthDisabled](arkts-mdm-restrictions-setfingerprintauthdisabled-f-sys.md#setfingerprintauthdisabled) | 禁用或启用指纹认证。 |
| [setHdcDisabled](arkts-mdm-restrictions-sethdcdisabled-f-sys.md#sethdcdisabled) | 使设备禁用或启用[HDC](docroot://../device-dev/subsystems/subsys-toolchain-hdc-guide.md)。使用callback异步回调。 |
| [setHdcDisabled](arkts-mdm-restrictions-sethdcdisabled-f-sys.md#sethdcdisabled-1) | 使设备禁用或启用HDC。使用Promise异步回调。 |
| [setPrinterDisabled](arkts-mdm-restrictions-setprinterdisabled-f-sys.md#setprinterdisabled) | 使设备禁用或启用打印能力。使用callback异步回调。 |
| [setPrinterDisabled](arkts-mdm-restrictions-setprinterdisabled-f-sys.md#setprinterdisabled-1) | 使设备禁用或启用打印能力。使用Promise异步回调。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FeatureForAccount](arkts-mdm-restrictions-featureforaccount-e.md) | 可为指定用户设置禁用/启用的特性的枚举。 |
| [FeatureForDevice](arkts-mdm-restrictions-featurefordevice-e.md) | 设备特性枚举。 |

