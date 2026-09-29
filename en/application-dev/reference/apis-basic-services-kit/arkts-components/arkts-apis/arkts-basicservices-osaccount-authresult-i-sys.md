# AuthResult (System API)

```TypeScript
interface AuthResult
```

Defines the authentication result information.

**Since:** 8

<!--Device-osAccount-interface AuthResult--><!--Device-osAccount-interface AuthResult-End-->

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

<!--Device-AuthResult-accountId?: int--><!--Device-AuthResult-accountId?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## credentialId

```TypeScript
credentialId?: Uint8Array
```

Credential ID, which is left blank by default.

**Type:** Uint8Array

**Since:** 12

<!--Device-AuthResult-credentialId?: Uint8Array--><!--Device-AuthResult-credentialId?: Uint8Array-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## freezingTime

```TypeScript
freezingTime?: number
```

Freezing time, in milliseconds. The default value is **-1**.

**Type:** number

**Since:** 8

<!--Device-AuthResult-freezingTime?: int--><!--Device-AuthResult-freezingTime?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## nextPhaseFreezingTime

```TypeScript
nextPhaseFreezingTime?: number
```

Next freezing time, in milliseconds. The default value is **undefined**.

**Type:** number

**Since:** 12

<!--Device-AuthResult-nextPhaseFreezingTime?: int--><!--Device-AuthResult-nextPhaseFreezingTime?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## pinValidityPeriod

```TypeScript
pinValidityPeriod?: number
```

Authentication validity period, in milliseconds. The default value is **undefined**.

**Type:** number

**Since:** 12

<!--Device-AuthResult-pinValidityPeriod?: long--><!--Device-AuthResult-pinValidityPeriod?: long-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## remainTimes

```TypeScript
remainTimes?: number
```

Number of remaining authentication times, which is **-1** by default.

**Type:** number

**Since:** 8

<!--Device-AuthResult-remainTimes?: int--><!--Device-AuthResult-remainTimes?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## token

```TypeScript
token?: Uint8Array
```

Authentication token, which is left blank by default.

**Type:** Uint8Array

**Since:** 8

<!--Device-AuthResult-token?: Uint8Array--><!--Device-AuthResult-token?: Uint8Array-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
