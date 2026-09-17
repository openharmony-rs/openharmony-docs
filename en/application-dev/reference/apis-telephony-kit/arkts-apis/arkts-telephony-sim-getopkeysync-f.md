# getOpKeySync

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getOpKeySync

```TypeScript
function getOpKeySync(slotId: number): string
```

Obtains the opkey of the SIM card in the specified slot.

**Since:** 10

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| string | opkey of the SIM card in the specified slot. |

**Examples**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let data: string = sim.getOpKeySync(0);
console.info(`getOpKey success, promise: data->${JSON.stringify(data)}`);
```
