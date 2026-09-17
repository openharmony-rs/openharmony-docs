# OsAccountSubProfile (System API)

Defines an OS account sub-profile.

**Since:** 26.0.0

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## createTime

```TypeScript
createTime: number
```

Time when the sub-profile was created. The value is a Unix timestamp (in milliseconds).

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## distributedInfo

```TypeScript
distributedInfo?: distributedAccount.DistributedInfo
```

Distributed account information bound to the OS account sub-profile. The default value is **undefined**.

**Type:** [distributedAccount.DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## id

```TypeScript
id: number
```

OS account sub-profile ID. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## index

```TypeScript
index: number
```

Location index of the OS account sub-profile. The value ranges from 0 to the number of sub-profiles minus 1. The index is unique under each OS account and is automatically allocated by the system when the sub-profile is created. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## osAccountLocalId

```TypeScript
osAccountLocalId: number
```

Local ID of the OS account of a sub-profile. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
