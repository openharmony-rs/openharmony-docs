# AuthResult (System API)

Defines the authentication result information.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## accountId

```TypeScript
accountId?: number
```

OS account ID, which is **undefined** by default.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## credentialId

```TypeScript
credentialId?: Uint8Array
```

Credential ID, which is left blank by default.

**Type:** Uint8Array

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## freezingTime

```TypeScript
freezingTime?: number
```

Freezing time, in milliseconds. The default value is **-1**.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## nextPhaseFreezingTime

```TypeScript
nextPhaseFreezingTime?: number
```

Next freezing time, in milliseconds. The default value is **undefined**.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## pinValidityPeriod

```TypeScript
pinValidityPeriod?: number
```

Authentication validity period, in milliseconds. The default value is **undefined**.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## remainTimes

```TypeScript
remainTimes?: number
```

Number of remaining authentication times, which is **-1** by default.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## token

```TypeScript
token?: Uint8Array
```

Authentication token, which is left blank by default.

**Type:** Uint8Array

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
