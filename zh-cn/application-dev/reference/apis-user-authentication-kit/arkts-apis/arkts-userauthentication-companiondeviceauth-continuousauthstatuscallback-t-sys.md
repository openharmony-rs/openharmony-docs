# ContinuousAuthStatusCallback（系统接口）

```TypeScript
type ContinuousAuthStatusCallback = (isAuthPassed: boolean, authTrustLevel?: UserAuth.AuthTrustLevel) => void
```

回调函数，用于接收持续认证状态变化通知。当伴随设备的认证状态发生变化时，系统会通过此回调通知应用当前的认证结果和认证可信等级。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-companionDeviceAuth-type ContinuousAuthStatusCallback = (isAuthPassed: boolean, authTrustLevel?: UserAuth.AuthTrustLevel) => void--><!--Device-companionDeviceAuth-type ContinuousAuthStatusCallback = (isAuthPassed: boolean, authTrustLevel?: UserAuth.AuthTrustLevel) => void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isAuthPassed | boolean | 是 | 认证是否通过。true表示伴随设备认证通过，用户身份已确认；false表示认证未通过，用户身份未确认或认证已失效。  |
| authTrustLevel | UserAuth.AuthTrustLevel | 否 | 伴随设备当前能达到的最高认证可信等级。值为ATL1（10000）、ATL2（20000）、ATL3（30000）或 ATL4（40000），等级越高表示认证安全性越强。 <br>**说明**： <br>仅当isAuthPassed为true时提供此参数。 <br>典型操作需要的身份认证可信等级，具体请参见 [认证可信等级划分原则](../../../security/UserAuthenticationKit/user-authentication-overview.md#生物认证可信等级划分原则)。  |

