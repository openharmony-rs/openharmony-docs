# AuthResultInfo

表示认证结果信息，用于描述认证结果。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [UserAuthResult](arkts-userauthentication-userauthresult-i.md)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## lockoutDuration

```TypeScript
lockoutDuration?: number
```

认证操作的锁定时长，时间单位为毫秒ms。

**类型：** number

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [lockoutDuration](arkts-userauthentication-authlockstate-i.md#lockoutduration)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## remainAttempts

```TypeScript
remainAttempts?: number
```

剩余的认证尝试次数。

**类型：** number

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [remainingAuthAttempts](arkts-userauthentication-authlockstate-i.md#remainingauthattempts)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## result

```TypeScript
result: number
```

认证结果。

**类型：** number

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [result](arkts-userauthentication-userauthresult-i.md#result)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## token

```TypeScript
token?: Uint8Array
```

用户身份认证通过的凭证。

**类型：** Uint8Array

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [token](arkts-userauthentication-userauthresult-i.md#token)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

