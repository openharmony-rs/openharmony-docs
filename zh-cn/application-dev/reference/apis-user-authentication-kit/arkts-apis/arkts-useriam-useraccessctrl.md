# @ohos.userIAM.userAccessCtrl

**userAccessCtrl**模块是OpenHarmony用户身份认证体系（UserIAM）的核心组件，专门用于认证令牌的验证和管理。该模块提供了验证认证令牌（AuthToken）的API，能够解析和验证用户身份认证结果，并返回 详细的认证信息。 该模块主要用于以下场景： - 系统级应用需要验证用户身份认证令牌的有效性，确保访问的安全性。 - 需要获取认证令牌的详细信息（如认证类型、信任级别、用户ID等），用于精确识别用户身份。 - 需要基于认证结果进行访问控制决策的场景，实现精细化权限管理。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace userAccessCtrl--><!--Device-unnamed-declare namespace userAccessCtrl-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [verifyAuthToken](arkts-userauthentication-useraccessctrl-verifyauthtoken-f-sys.md#verifyauthtoken) | 验证认证令牌。该接口用于校验AuthToken的有效性，包括完整性校验和时效性校验，校验通过后返回解析后的AuthToken详细信息。使用Promise异步回调。 完整性校验通过验证AuthToken的数字签名确保令牌未被篡改；时效性校验通过比对AuthToken的签发时间与当前时间，并结合allowableDuration参数判断令牌是否在有效期内。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthToken](arkts-userauthentication-useraccessctrl-authtoken-i-sys.md) | 认证令牌数据。表示校验通过后返回解析后的AuthToken数据，包含认证的详细信息，如挑战值、认证信任等级、认证类型、用户ID等。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthTokenType](arkts-userauthentication-useraccessctrl-authtokentype-e-sys.md) | 认证令牌类型枚举。该枚举定义了认证令牌的类型，用于标识令牌的签发来源。 |
<!--DelEnd-->

