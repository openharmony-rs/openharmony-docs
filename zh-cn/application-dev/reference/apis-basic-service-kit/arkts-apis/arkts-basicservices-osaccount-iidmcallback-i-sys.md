# IIdmCallback（系统接口）

表示身份管理回调类。

**起始版本：** 8

<!--Device-osAccount-interface IIdmCallback--><!--Device-osAccount-interface IIdmCallback-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## onAcquireInfo

```TypeScript
onAcquireInfo?: (module: number, acquire: number, extraInfo: Uint8Array) => void
```

身份管理信息获取回调函数。

**类型：** (module: number, acquire: number, extraInfo: Uint8Array) =&gt; void

**起始版本：** 8

<!--Device-IIdmCallback-onAcquireInfo?: (module: int, acquire: int, extraInfo: Uint8Array) => void--><!--Device-IIdmCallback-onAcquireInfo?: (module: int, acquire: int, extraInfo: Uint8Array) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## onResult

```TypeScript
onResult: (result: number, extraInfo: RequestResult) => void
```

身份管理操作结果回调函数，返回结果码和请求结果信息。

**类型：** (result: number, extraInfo: RequestResult) =&gt; void

**起始版本：** 8

<!--Device-IIdmCallback-onResult: (result: int, extraInfo: RequestResult) => void--><!--Device-IIdmCallback-onResult: (result: int, extraInfo: RequestResult) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

