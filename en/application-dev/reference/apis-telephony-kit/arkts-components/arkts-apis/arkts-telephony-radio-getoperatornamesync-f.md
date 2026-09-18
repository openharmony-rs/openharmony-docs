# getOperatorNameSync

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## getOperatorNameSync

```TypeScript
function getOperatorNameSync(slotId: number): string
```

Obtains the carrier name of the SIM card in the specified slot.

**Since:** 10

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| string | Carrier name, for example, China Mobile. |

**Examples**

```TypeScript
let slotId: number = 0;
let operatorName: string = radio.getOperatorNameSync(slotId);
console.info(`operator name is:` + operatorName);
```
