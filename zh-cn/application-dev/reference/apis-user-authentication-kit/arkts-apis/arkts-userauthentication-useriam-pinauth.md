# @ohos.userIAM.pinAuth(PIN Authentication)

**pinAuthManager**模块是OpenHarmony用户身份和访问管理(UserIAM系统）。专用于PIN认证管理。本模块提供系统应用配置PIN码认证的安全策略接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace pinAuth--><!--Device-unnamed-declare namespace pinAuth-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { pinAuth } from '@kit.UserAuthenticationKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getPinComplexityPolicy](arkts-userauthentication-pinauth-getpincomplexitypolicy-f-sys.md#getpincomplexitypolicy-1) | 获取PIN复杂度检查策略和描述。 |
| [getPinDeletionDisabledState](arkts-userauthentication-pinauth-getpindeletiondisabledstate-f-sys.md#getpindeletiondisabledstate-1) | 获取PIN删除功能的禁用状态。 |
| [getPinValidityPeriod](arkts-userauthentication-pinauth-getpinvalidityperiod-f-sys.md#getpinvalidityperiod-1) | 获取PIN有效期。 |
| [setPinComplexityPolicy](arkts-userauthentication-pinauth-setpincomplexitypolicy-f-sys.md#setpincomplexitypolicy-1) | 设置PIN码复杂度检查策略和描述信息。设置策略后，用户新注册和修改的锁屏密码必须匹配指定的复杂度正则表达式。 |
| [setPinDeletionDisabledState](arkts-userauthentication-pinauth-setpindeletiondisabledstate-f-sys.md#setpindeletiondisabledstate-1) | 设置PIN删除功能的禁用状态。策略设置完成后，用户功能禁用时，无法删除PIN。 |
| [setPinValidityPeriod](arkts-userauthentication-pinauth-setpinvalidityperiod-f-sys.md#setpinvalidityperiod-1) | 设置PIN有效期。设置策略后，当口令过期时，会弹出安全提示要求用户重置口令。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PinComplexityPolicy](arkts-userauthentication-pinauth-pincomplexitypolicy-i-sys.md) | PIN码复杂度检查策略及说明。 |
<!--DelEnd-->
