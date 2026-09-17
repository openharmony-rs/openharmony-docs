# OsAccountSwitchEventData (System API)

Defines the event that indicates the start or end of a foreground-background OS account switchover.

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## displayId

```TypeScript
displayId?: number
```

ID of the logical display where the switchover occurs. The default value is **0**.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## fromAccountId

```TypeScript
fromAccountId: number
```

ID of the source OS account.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## toAccountId

```TypeScript
toAccountId: number
```

ID of the target OS account.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
