# @ohos.enterprise.restrictions

本模块提供设置通用限制类策略能力。可以全局禁用和解除禁用蓝牙、HDC、USB、Wi-Fi、蜂窝数据、相机、麦克风等特性。 **使用场景**： - 企业设备管理场景下，管理员需要对员工设备进行功能限制，防止数据泄露或非授权使用。 - BYOD（Bring Your Own Device）场景下，企业空间需要限制设备功能以符合企业安全策略。 - 设备安全管控场景下，需要禁用特定功能以保护企业敏感信息。 **能解决的问题**： - 防止员工通过蓝牙、USB等方式传输企业敏感数据。 - 限制设备调试能力（HDC）以提升设备安全性。 - 控制网络访问能力（Wi-Fi、蜂窝数据等）以符合企业网络策略。 - 管理设备多媒体能力（相机、麦克风等）以保护隐私和企业机密。 **带来的收益**： - 提升企业设备安全性，降低数据泄露风险。 - 满足企业合规要求，符合安全审计标准。 - 实现精细化的设备功能管控，平衡安全与使用体验。 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare namespace restrictions--><!--Device-unnamed-declare namespace restrictions-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addDisallowedListForAccount](arkts-mdm-restrictions-adddisallowedlistforaccount-f.md#addDisallowedListForAccount) | 为指定用户添加禁止使用某特性的应用名单。指定用户下，添加到名单中的应用不允许使用指定的特性能力。 |
| [getDisallowedListForAccount](arkts-mdm-restrictions-getdisallowedlistforaccount-f.md#getDisallowedListForAccount) | 获取指定用户禁止使用某特性的应用名单。 |
| [getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy) | 查询某特性是否被禁用。 |
| [getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy) | 查询指定设备特性是否被禁用。 |
| [getDisallowedPolicyForAccount](arkts-mdm-restrictions-getdisallowedpolicyforaccount-f.md#getDisallowedPolicyForAccount) | 获取指定用户的某特性状态。 |
| [getDisallowedPolicyForAccount](arkts-mdm-restrictions-getdisallowedpolicyforaccount-f.md#getDisallowedPolicyForAccount) | 获取指定用户的某特性状态。 |
| [getUserRestricted](arkts-mdm-restrictions-getuserrestricted-f.md#getUserRestricted) | 获取设置项的禁用状态。 |
| [getUserRestricted](arkts-mdm-restrictions-getuserrestricted-f.md#getUserRestricted) | 获取设置项的禁用状态 |
| [getUserRestrictedForAccount](arkts-mdm-restrictions-getuserrestrictedforaccount-f.md#getUserRestrictedForAccount) | 获取指定用户设置项的禁用状态。 |
| [getUserRestrictedForAccount](arkts-mdm-restrictions-getuserrestrictedforaccount-f.md#getUserRestrictedForAccount) | 获取指定用户设置项的禁用状态。 |
| [removeDisallowedListForAccount](arkts-mdm-restrictions-removedisallowedlistforaccount-f.md#removeDisallowedListForAccount) | 为指定用户移除禁止使用某特性的应用名单。 |
| [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy) | 设置禁用/启用某特性。 |
| [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy) | 设置禁用/启用指定设备特性，禁用后相关设备特性无法被使用。 |
| [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount) | 设置禁用/启用指定用户的某特性。 |
| [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount) | 设置禁用/启用指定用户的某特性。 |
| [setUserRestriction](arkts-mdm-restrictions-setuserrestriction-f.md#setUserRestriction) | 设置用户行为的限制规则。 |
| [setUserRestriction](arkts-mdm-restrictions-setuserrestriction-f.md#setUserRestriction) | 设置用户行为的限制规则。 |
| [setUserRestrictionForAccount](arkts-mdm-restrictions-setuserrestrictionforaccount-f.md#setUserRestrictionForAccount) | 设置指定用户行为的限制规则。 |
| [setUserRestrictionForAccount](arkts-mdm-restrictions-setuserrestrictionforaccount-f.md#setUserRestrictionForAccount) | 限制指定用户修改指定的设置项。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disableMicrophone](arkts-mdm-restrictions-disablemicrophone-f-sys.md#disableMicrophone) | 使设备禁用或启用麦克风。 |
| [isFingerprintAuthDisabled](arkts-mdm-restrictions-isfingerprintauthdisabled-f-sys.md#isFingerprintAuthDisabled) | 查询指纹认证是否被禁用。 |
| [isHdcDisabled](arkts-mdm-restrictions-ishdcdisabled-f-sys.md#isHdcDisabled) | 查询HDC是否被禁用。使用callback异步回调。 |
| [isHdcDisabled](arkts-mdm-restrictions-ishdcdisabled-f-sys.md#isHdcDisabled（系统接口）) | 查询HDC是否被禁用。使用Promise异步回调。 |
| [isMicrophoneDisabled](arkts-mdm-restrictions-ismicrophonedisabled-f-sys.md#isMicrophoneDisabled) | 查询麦克风是否被禁用。 |
| [isPrinterDisabled](arkts-mdm-restrictions-isprinterdisabled-f-sys.md#isPrinterDisabled) | 查询设备打印能力是否被禁用。使用callback异步回调。 |
| [isPrinterDisabled](arkts-mdm-restrictions-isprinterdisabled-f-sys.md#isPrinterDisabled（系统接口）) | 查询设备打印能力是否被禁用。使用Promise异步回调。 |
| [setFingerprintAuthDisabled](arkts-mdm-restrictions-setfingerprintauthdisabled-f-sys.md#setFingerprintAuthDisabled) | 禁用或启用指纹认证。 |
| [setHdcDisabled](arkts-mdm-restrictions-sethdcdisabled-f-sys.md#setHdcDisabled) | 使设备禁用或启用[HDC](../../../../device-dev/subsystems/subsys-toolchain-hdc-guide.md)。使用callback异步回调。 |
| [setHdcDisabled](arkts-mdm-restrictions-sethdcdisabled-f-sys.md#setHdcDisabled（系统接口）) | 使设备禁用或启用HDC。使用Promise异步回调。 |
| [setPrinterDisabled](arkts-mdm-restrictions-setprinterdisabled-f-sys.md#setPrinterDisabled) | 使设备禁用或启用打印能力。使用callback异步回调。 |
| [setPrinterDisabled](arkts-mdm-restrictions-setprinterdisabled-f-sys.md#setPrinterDisabled（系统接口）) | 使设备禁用或启用打印能力。使用Promise异步回调。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FeatureForAccount](arkts-mdm-restrictions-featureforaccount-e.md) | 可为指定用户设置禁用/启用的特性的枚举。 |
| [FeatureForDevice](arkts-mdm-restrictions-featurefordevice-e.md) | 设备特性枚举。 |
| [SettingsForAccount](arkts-mdm-restrictions-settingsforaccount-e.md) | 用户设置项枚举。 |
| [SettingsForDevice](arkts-mdm-restrictions-settingsfordevice-e.md) | 设备设置项枚举。 |

