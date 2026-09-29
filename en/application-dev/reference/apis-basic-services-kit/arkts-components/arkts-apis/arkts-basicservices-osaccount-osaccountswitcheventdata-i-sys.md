# OsAccountSwitchEventData (System API)

```TypeScript
interface OsAccountSwitchEventData
```

Defines the event that indicates the start or end of a foreground-background OS account switchover.

**Since:** 12

<!--Device-osAccount-interface OsAccountSwitchEventData--><!--Device-osAccount-interface OsAccountSwitchEventData-End-->

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

<!--Device-OsAccountSwitchEventData-displayId?: long--><!--Device-OsAccountSwitchEventData-displayId?: long-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## fromAccountId

```TypeScript
fromAccountId: number
```

ID of the source OS account.

**Type:** number

**Since:** 12

<!--Device-OsAccountSwitchEventData-fromAccountId: int--><!--Device-OsAccountSwitchEventData-fromAccountId: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## toAccountId

```TypeScript
toAccountId: number
```

ID of the target OS account.

**Type:** number

**Since:** 12

<!--Device-OsAccountSwitchEventData-toAccountId: int--><!--Device-OsAccountSwitchEventData-toAccountId: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
