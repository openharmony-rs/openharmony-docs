# IUserAuthCallback

返回认证结果的回调对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [AuthEvent](arkts-userauthentication-authevent-i.md)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## onAcquireInfo

```TypeScript
onAcquireInfo?: (module: number, acquire: number, extraInfo: any) => void
```

回调函数，返回认证过程中的提示信息，非必须实现。

- **module**: 发送提示信息的模块标识。
- **acquire**: 认证执过程中的提示信息。
- **extraInfo**: 预留字段。

**类型：** (module: number, acquire: number, extraInfo: any) => void

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [callback](arkts-userauthentication-authevent-i.md#callback-1)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## onResult

```TypeScript
onResult: (result: number, extraInfo: AuthResult) => void
```

回调函数，返回认证结果。

- **result**: 认证结果，参见[ResultCode](arkts-userauthentication-resultcode-e.md)。
- **extraInfo**: 扩展信息，不同情况下的具体信息。如果身份验证通过，则在extraInfo中返回用户认证令牌；如果身份验证失败，则在extraInfo中返回剩余的用户认证次数；如果身份验证执行器被锁定，则在
extraInfo中返回冻结时间，类型为[AuthResult](arkts-userauthentication-authresult-i.md)。

**类型：** (result: number, extraInfo: AuthResult) => void

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [callback](arkts-userauthentication-authevent-i.md#callback-1)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

