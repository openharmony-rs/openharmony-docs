# DistributedInfo

```TypeScript
interface DistributedInfo
```

Represents the distributed account information about an OS account.

**Since:** 7

<!--Device-distributedAccount-interface DistributedInfo--><!--Device-distributedAccount-interface DistributedInfo-End-->

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { distributedAccount } from '@kit.BasicServicesKit';
```

## avatar

```TypeScript
avatar?: string
```

Avatar of the distributed account. Set this parameter when the user avatar needs to be displayed. If this parameter is not set, it is left empty by default, which does not affect the account function.

**Type:** string

**Since:** 9

<!--Device-DistributedInfo-avatar?: string--><!--Device-DistributedInfo-avatar?: string-End-->

**System capability:** SystemCapability.Account.OsAccount

## event

```TypeScript
event: string
```

Login state of the distributed account. The state can be login, logout, token invalid, or logoff, which correspond to the following strings respectively:

- Ohos.account.event.LOGIN

- Ohos.account.event.LOGOUT

- Ohos.account.event.TOKEN_INVALID

- Ohos.account.event.LOGOFF

**Type:** string

**Since:** 7

<!--Device-DistributedInfo-event: string--><!--Device-DistributedInfo-event: string-End-->

**System capability:** SystemCapability.Account.OsAccount

## id

```TypeScript
id: string
```

UID of the distributed account. It must be a non-null string.

**Type:** string

**Since:** 7

<!--Device-DistributedInfo-id: string--><!--Device-DistributedInfo-id: string-End-->

**System capability:** SystemCapability.Account.OsAccount

## name

```TypeScript
name: string
```

Name of the distributed account. It must be a non-null string.

**Type:** string

**Since:** 7

<!--Device-DistributedInfo-name: string--><!--Device-DistributedInfo-name: string-End-->

**System capability:** SystemCapability.Account.OsAccount

## nickname

```TypeScript
nickname?: string
```

Nickname of the distributed account. Set this parameter when the user nickname needs to be displayed. If this parameter is not set, it is left empty by default, which does not affect the account function.

**Type:** string

**Since:** 9

<!--Device-DistributedInfo-nickname?: string--><!--Device-DistributedInfo-nickname?: string-End-->

**System capability:** SystemCapability.Account.OsAccount

## scalableData

```TypeScript
scalableData?: object
```

Scalable data about the distributed account. Set this parameter when customized service information needs to be passed in key-value (KV) pairs. If this parameter is not set, it is left empty by default, which does not affect the basic account function.

**Type:** object

**Since:** 8

<!--Device-DistributedInfo-scalableData?: object--><!--Device-DistributedInfo-scalableData?: object-End-->

**System capability:** SystemCapability.Account.OsAccount

## status

```TypeScript
readonly status?: DistributedAccountStatus
```

Status of the distributed account. The value is of the enumerated type. This parameter is used when the account login status needs to be queried or set. If this parameter is not set, the default value is **NOT_LOGGED_IN** (not logged in).

**Type:** [DistributedAccountStatus](arkts-basicservices-distributedaccount-distributedaccountstatus-e.md)

**Since:** 10

<!--Device-DistributedInfo-readonly status?: DistributedAccountStatus--><!--Device-DistributedInfo-readonly status?: DistributedAccountStatus-End-->

**System capability:** SystemCapability.Account.OsAccount
