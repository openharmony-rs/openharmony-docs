# IUserAuthCallback（系统接口）

表示用户认证回调类。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-osAccount-interface IUserAuthCallback--><!--Device-osAccount-interface IUserAuthCallback-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## onAcquireInfo

```TypeScript
onAcquireInfo?: (module: int, acquire: int, extraInfo: Uint8Array) => void
```

身份认证信息获取回调函数。

**类型：** (module: int, acquire: int, extraInfo: Uint8Array) =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-IUserAuthCallback-onAcquireInfo?: (module: int, acquire: int, extraInfo: Uint8Array) => void--><!--Device-IUserAuthCallback-onAcquireInfo?: (module: int, acquire: int, extraInfo: Uint8Array) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## onResult

```TypeScript
onResult: (result: int, extraInfo: AuthResult) => void
```

身份认证结果回调函数，返回结果码和认证结果信息。

**类型：** (result: int, extraInfo: AuthResult) =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-IUserAuthCallback-onResult: (result: int, extraInfo: AuthResult) => void--><!--Device-IUserAuthCallback-onResult: (result: int, extraInfo: AuthResult) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

