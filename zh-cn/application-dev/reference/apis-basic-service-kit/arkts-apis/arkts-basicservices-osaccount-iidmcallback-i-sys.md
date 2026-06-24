# IIdmCallback（系统接口）

表示身份管理回调类。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## onAcquireInfo

```TypeScript
onAcquireInfo?: (module: number, acquire: number, extraInfo: Uint8Array) => void
```

身份管理信息获取回调函数。

**类型：** (module: number, acquire: number, extraInfo: Uint8Array) => void

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## onResult

```TypeScript
onResult: (result: number, extraInfo: RequestResult) => void
```

身份管理操作结果回调函数，返回结果码和请求结果信息。

**类型：** (result: number, extraInfo: RequestResult) => void

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

