# DistributedInfo

提供操作系统账号的分布式账号信息。

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { distributedAccount } from '@kit.BasicServicesKit';
```

## avatar

```TypeScript
avatar?: string
```

分布式账号的头像，当需要显示用户头像时设置。不设置时默认为空，不影响账号功能使用。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

## event

```TypeScript
event: string
```

分布式账号登录状态，包括登录、登出、Token失效和注销，分别对应以下字符串：

- Ohos.account.event.LOGIN

- Ohos.account.event.LOGOUT

- Ohos.account.event.TOKEN_INVALID

- Ohos.account.event.LOGOFF

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## id

```TypeScript
id: string
```

分布式账号UID，非空字符串。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## name

```TypeScript
name: string
```

分布式账号名称，非空字符串。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## nickname

```TypeScript
nickname?: string
```

分布式账号的昵称，当需要显示用户昵称时设置。不设置时默认为空，不影响账号功能使用。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

## scalableData

```TypeScript
scalableData?: object
```

分布式账号扩展信息，当需要传递定制化业务信息时设置，以k-v形式传递。不设置时默认为空，不影响账号基本功能。

**类型：** object

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

## status

```TypeScript
readonly status?: DistributedAccountStatus
```

分布式账号的状态，枚举类型。当需要查询或设置账号登录状态时使用。不设置时默认为NOT_LOGGED_IN（未登录状态）。

**类型：** [DistributedAccountStatus](arkts-basicservices-distributedaccount-distributedaccountstatus-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.Account.OsAccount
