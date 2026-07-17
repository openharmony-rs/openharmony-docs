# AuthLockState

认证类型的身份认证冻结状态。该接口用于查询指定认证类型（如人脸、指纹、PIN）当前的冻结状态，包括是否被冻结、剩余尝试次数和冻结时长等信息。当用户多次认证不通过后，认证器可能进入临时冻结或永久冻结状态，应用可根据冻结信息提示用户。

**起始版本：** 22

<!--Device-userAuth-interface AuthLockState--><!--Device-userAuth-interface AuthLockState-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## isLocked

```TypeScript
isLocked: boolean
```

表示认证是否已被冻结。true表示已冻结，此时用户无法使用该认证类型进行身份认证；false表示未冻结，用户可以正常使用该认证类型。冻结状态通常由连续多次认证不通过触发。

**类型：** boolean

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AuthLockState-isLocked: boolean--><!--Device-AuthLockState-isLocked: boolean-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## lockoutDuration

```TypeScript
lockoutDuration: number
```

认证被冻结时的剩余冻结时间，单位为毫秒。此字段仅在isLocked为true时有效。

当永久冻结时，值为[PERMANENT_LOCKOUT_DURATION](arkts-userauthentication-userauth-con.md#permanent_lockout_duration)，表示认证器已永久锁定，需要用户通过PIN认证解锁后才能继续使用该认证类型。临时冻结时，该值为实际的剩余冻结时长，冻结结束后用户可继续尝试认证。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AuthLockState-lockoutDuration: int--><!--Device-AuthLockState-lockoutDuration: int-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## remainingAuthAttempts

```TypeScript
remainingAuthAttempts: number
```

认证未被冻结时的剩余尝试次数，最大为5次。每次认证不通过后该值会递减，当降为0时认证器将进入冻结状态。此字段仅在isLocked为false时有效。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AuthLockState-remainingAuthAttempts: int--><!--Device-AuthLockState-remainingAuthAttempts: int-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

