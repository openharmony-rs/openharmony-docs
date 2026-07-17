# AuthResult

表示认证结果的对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [AuthResultInfo](arkts-userauthentication-userauth-authresultinfo-i.md)

<!--Device-userAuth-interface AuthResult--><!--Device-userAuth-interface AuthResult-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## freezingTime

```TypeScript
freezingTime?: number
```

认证操作的冻结时间。单位为毫秒。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [lockoutDuration](arkts-userauthentication-userauth-authresultinfo-i.md#lockoutduration)

<!--Device-AuthResult-freezingTime?: number--><!--Device-AuthResult-freezingTime?: number-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## remainTimes

```TypeScript
remainTimes?: number
```

剩余的认证操作次数。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [remainAttempts](arkts-userauthentication-userauth-authresultinfo-i.md#remainattempts)

<!--Device-AuthResult-remainTimes?: number--><!--Device-AuthResult-remainTimes?: number-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## token

```TypeScript
token?: Uint8Array
```

认证通过的令牌信息。

**类型：** Uint8Array

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [token](arkts-userauthentication-userauth-authresultinfo-i.md#token)

<!--Device-AuthResult-token?: Uint8Array--><!--Device-AuthResult-token?: Uint8Array-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

