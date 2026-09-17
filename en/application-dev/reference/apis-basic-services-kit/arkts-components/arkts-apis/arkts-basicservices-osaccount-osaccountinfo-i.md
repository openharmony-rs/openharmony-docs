# OsAccountInfo

Represents the OS account information.

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## constraints

```TypeScript
constraints: Array<string>
```

[Constraints](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md) of the OS account. By default, no value is passed in.

**Type:** Array&lt;string&gt;

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

## createTime

```TypeScript
createTime: number
```

OS account creation time. The value is a Unix timestamp (in seconds).

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

## distributedInfo

```TypeScript
distributedInfo: distributedAccount.DistributedInfo
```

Distributed account information. By default, no value is passed in.

**Type:** [distributedAccount.DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md)

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

## domainInfo

```TypeScript
domainInfo: DomainAccountInfo
```

Domain account information. By default, no value is passed in.

**Type:** [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md)

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

## isActivated

```TypeScript
isActivated: boolean
```

Whether the OS account is activated. The value **true** means the specified account is activated; the value **false** means the opposite.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Account.OsAccount

## isActived

```TypeScript
isActived: boolean
```

Whether the OS account is activated. The value **true** means the specified account is activated; the value **false** means the opposite.

Note: This parameter is supported since API version 7 and deprecated since API version 11. You are advised to use **isActivated** instead.

**Type:** boolean

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [isActivated](#isactivated)

**System capability:** SystemCapability.Account.OsAccount

## isCreateCompleted

```TypeScript
isCreateCompleted: boolean
```

Whether the OS account information is complete. The value **true** means the specified account is complete; the value **false** means the opposite.

**Type:** boolean

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

## isUnlocked

```TypeScript
isUnlocked: boolean
```

Whether the account is unlocked (whether the **el2/** directory is decrypted). The value **true** means the specified account is unlocked; the value **false** means the opposite.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Account.OsAccount

## isVerified

```TypeScript
isVerified: boolean
```

Whether the account has been verified. The value **true** means the specified account has been verified; the value **false** means the opposite.

**Type:** boolean

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [isUnlocked](#isunlocked)

**System capability:** SystemCapability.Account.OsAccount

## lastLoginTime

```TypeScript
lastLoginTime: number
```

Last login time of the OS account. The value is a Unix timestamp (in seconds).

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

## localId

```TypeScript
localId: number
```

ID of the target OS account.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

## localName

```TypeScript
localName: string
```

Name of the OS account.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

## photo

```TypeScript
photo: string
```

Avatar of the OS account. By default, no value is passed in.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

## serialNumber

```TypeScript
serialNumber: number
```

SN of the OS account.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

## type

```TypeScript
type: OsAccountType
```

Type of the OS account.

**Type:** [OsAccountType](arkts-basicservices-osaccount-osaccounttype-e.md)

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount
