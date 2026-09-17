# hasSimCardSync

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## hasSimCardSync

```TypeScript
function hasSimCardSync(slotId: number): boolean
```

Checks whether the SIM card in the specified slot is installed.

**Since:** 10

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the SIM card in the specified slot is installed.<br>- **true**: installed. <br>- **false**: not installed. |

**Examples**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let hasSimCard: boolean = sim.hasSimCardSync(0);
console.info(`has sim card: ` + hasSimCard);
```
