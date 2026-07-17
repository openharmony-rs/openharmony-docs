# AuthResultInfo

表示认证结果信息，用于描述认证结果。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [UserAuthResult](arkts-userauthentication-userauth-userauthresult-i.md)

<!--Device-userAuth-interface AuthResultInfo--><!--Device-userAuth-interface AuthResultInfo-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## lockoutDuration

```TypeScript
lockoutDuration?: number
```

认证操作的锁定时长，时间单位为毫秒ms。

**类型：** number

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [lockoutDuration](arkts-userauthentication-userauth-authlockstate-i.md#lockoutduration)

<!--Device-AuthResultInfo-lockoutDuration?: number--><!--Device-AuthResultInfo-lockoutDuration?: number-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## remainAttempts

```TypeScript
remainAttempts?: number
```

剩余的认证尝试次数。

**类型：** number

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [remainingAuthAttempts](arkts-userauthentication-userauth-authlockstate-i.md#remainingauthattempts)

<!--Device-AuthResultInfo-remainAttempts?: number--><!--Device-AuthResultInfo-remainAttempts?: number-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## result

```TypeScript
result: number
```

认证结果。

**类型：** number

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [result](arkts-userauthentication-userauth-userauthresult-i.md#result)

<!--Device-AuthResultInfo-result: number--><!--Device-AuthResultInfo-result: number-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## token

```TypeScript
token?: Uint8Array
```

用户身份认证通过的凭证。

**类型：** Uint8Array

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [token](arkts-userauthentication-userauth-userauthresult-i.md#token)

<!--Device-AuthResultInfo-token?: Uint8Array--><!--Device-AuthResultInfo-token?: Uint8Array-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

