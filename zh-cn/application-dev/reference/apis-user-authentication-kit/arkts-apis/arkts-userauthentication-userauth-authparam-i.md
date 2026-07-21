# AuthParam

用户认证相关参数。该接口用于配置用户认证的各项参数，包括挑战值、认证类型列表、认证信任等级、认证结果复用配置等。通过合理配置这些参数，可以满足不同业务场景下的认证需求。

**起始版本：** 10

<!--Device-userAuth-interface AuthParam--><!--Device-userAuth-interface AuthParam-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## authTrustLevel

```TypeScript
authTrustLevel: AuthTrustLevel
```

期望达到的认证可信等级。认证可信等级决定了认证的安全强度，应根据业务场景的安全需求选择合适的等级：

- ATL1：适用于业务风控、一般个人数据查询等低安全场景。  
- ATL2：适用于应用登录、维持设备解锁状态等中等安全场景。  
- ATL3：适用于设备解锁等较高安全场景。  
- ATL4：适用于小额支付等高安全场景。

典型操作需要的身份认证可信等级，以及身份认证可信等级的划分请参见[认证可信等级划分原则](../../../security/UserAuthenticationKit/user-authentication-overview.md#生物认证可信等级划分原则)。

**类型：** AuthTrustLevel

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AuthParam-authTrustLevel: AuthTrustLevel--><!--Device-AuthParam-authTrustLevel: AuthTrustLevel-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## authType

```TypeScript
authType: UserAuthType[]
```

认证类型列表，用来指定用户认证界面提供的认证方法。可同时指定多种认证类型，如[UserAuthType.PIN, UserAuthType.FACE, UserAuthType.FINGERPRINT]，用户可选择任意一种完成认证。认证类型的选择会影响认证结果复用的匹配条件。暂不支持同时发起伴随设备认证和其他认证类型。

**类型：** UserAuthType[]

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AuthParam-authType: UserAuthType[]--><!--Device-AuthParam-authType: UserAuthType[]-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## challenge

```TypeScript
challenge: Uint8Array
```

随机挑战值，可用于防重放攻击。最大长度为32字节，可传Uint8Array([])。建议使用[加解密算法库框架](../../apis-crypto-architecture-kit/arkts-apis/arkts-security-cryptoframework.md)生成的随机数作为挑战值，以增强安全性。认证通过后，挑战值会被包含在认证令牌中，业务可通过验证令牌中的挑战值来确认认证结果的有效性。

**类型：** Uint8Array

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AuthParam-challenge: Uint8Array--><!--Device-AuthParam-challenge: Uint8Array-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## reuseUnlockResult

```TypeScript
reuseUnlockResult?: ReuseUnlockResult
```

表示可以复用解锁认证的结果。配置后，若满足复用条件，系统将直接返回之前的认证结果，无需用户再次进行认证交互。默认为不复用。启用认证结果复用可以提升用户体验，但应根据业务场景的安全需求合理配置复用模式和有效时长。

**类型：** ReuseUnlockResult

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AuthParam-reuseUnlockResult?: ReuseUnlockResult--><!--Device-AuthParam-reuseUnlockResult?: ReuseUnlockResult-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## skipLockedBiometricAuth

```TypeScript
skipLockedBiometricAuth?: boolean
```

是否跳过已禁用的认证方式自动切换至其它方式的认证。若无可切换的认证方式则关闭控件，返回认证冻结错误码。

- true：生物认证冻结时，跳过倒计时界面直接切换到其他方式的认证（如从冻结的指纹切换到人脸或PIN）。适用于希望快速完成认证的场景。  
- false（默认）：不跳过，用户需要等待冻结倒计时结束后才能继续尝试该认证方式或手动切换。

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AuthParam-skipLockedBiometricAuth?: boolean--><!--Device-AuthParam-skipLockedBiometricAuth?: boolean-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

