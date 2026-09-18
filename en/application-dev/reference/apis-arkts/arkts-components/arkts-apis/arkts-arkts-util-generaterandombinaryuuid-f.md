# generateRandomBinaryUUID

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## generateRandomBinaryUUID

```TypeScript
function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array
```

Uses a secure random number generator to generate a random universally unique identifier (UUID) of RFC 4122 version 4.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| entropyCache | boolean | No | Whether to use a cached UUID. The value **true** means to use a cached UUID, and **false** means the opposite. The default value is **true**. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | A Uint8Array value representing the UUID generated. |

**Examples**

```TypeScript
let uuid = util.generateRandomBinaryUUID(true);
console.info(JSON.stringify(uuid));
// Output a random UUID.
```
