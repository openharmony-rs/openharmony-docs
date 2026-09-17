# getSimSpnSync

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getSimSpnSync

```TypeScript
function getSimSpnSync(slotId: number): string
```

Obtains the SPN of the SIM card in the specified slot. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| string | SPN of the SIM card in the specified slot. |

**Examples**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let spn: string = sim.getSimSpnSync(0);
console.info(`the sim card spn is:` + spn);
```
