# AuthUser

Represents the user authorization information.

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## authAccount

```TypeScript
authAccount: string
```

Account of the user who can access the DLP file. The value contains a maximum of 255 bytes. If the value is out of range, error code 401 is thrown.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## authAccountType

```TypeScript
authAccountType: AccountType
```

Type of the account.

**Type:** [AccountType](arkts-dataprotection-dlppermission-accounttype-e.md)

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## dlpFileAccess

```TypeScript
dlpFileAccess: DLPFileAccess
```

Permission granted to the user.

**Type:** [DLPFileAccess](arkts-dataprotection-dlppermission-dlpfileaccess-e.md)

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## permExpiryTime

```TypeScript
permExpiryTime: number
```

Time when the authorization expires. The value must be greater than or equal to 0. If the value is out of range, it will be forcibly converted to an unsigned integer. Unit: s.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention
