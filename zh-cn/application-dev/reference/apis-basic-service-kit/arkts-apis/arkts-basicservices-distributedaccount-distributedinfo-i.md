# DistributedInfo

提供操作系统账号的分布式信息。

**起始版本：** 7

<!--Device-distributedAccount-interface DistributedInfo--><!--Device-distributedAccount-interface DistributedInfo-End-->

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { distributedAccount } from '@kit.BasicServicesKit';
```

## avatar

```TypeScript
avatar?: string
```

分布式账号的头像，默认为空。

**类型：** string

**起始版本：** 9

<!--Device-DistributedInfo-avatar?: string--><!--Device-DistributedInfo-avatar?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

## event

```TypeScript
event: string
```

分布式账号登录状态，包括登录、登出、Token失效和注销，分别对应以下字符串：

- Ohos.account.event.LOGIN

- Ohos.account.event.LOGOUT

- Ohos.account.event.TOKEN_INVALID

- Ohos.account.event.LOGOFF

**类型：** string

**起始版本：** 7

<!--Device-DistributedInfo-event: string--><!--Device-DistributedInfo-event: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

## id

```TypeScript
id: string
```

分布式账号UID，非空字符串。

**类型：** string

**起始版本：** 7

<!--Device-DistributedInfo-id: string--><!--Device-DistributedInfo-id: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

## name

```TypeScript
name: string
```

分布式账号名称，非空字符串。

**类型：** string

**起始版本：** 7

<!--Device-DistributedInfo-name: string--><!--Device-DistributedInfo-name: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

## nickname

```TypeScript
nickname?: string
```

分布式账号的昵称，默认为空。

**类型：** string

**起始版本：** 9

<!--Device-DistributedInfo-nickname?: string--><!--Device-DistributedInfo-nickname?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

## scalableData

```TypeScript
scalableData?: object
```

分布式账号扩展信息，根据业务所需，以k-v形式传递定制化信息，默认为空。

**类型：** object

**起始版本：** 8

<!--Device-DistributedInfo-scalableData?: object--><!--Device-DistributedInfo-scalableData?: object-End-->

**系统能力：** SystemCapability.Account.OsAccount

## status

```TypeScript
readonly status?: DistributedAccountStatus
```

分布式账号的状态，枚举类型，默认为未登录状态。

**类型：** DistributedAccountStatus

**起始版本：** 10

<!--Device-DistributedInfo-readonly status?: DistributedAccountStatus--><!--Device-DistributedInfo-readonly status?: DistributedAccountStatus-End-->

**系统能力：** SystemCapability.Account.OsAccount

