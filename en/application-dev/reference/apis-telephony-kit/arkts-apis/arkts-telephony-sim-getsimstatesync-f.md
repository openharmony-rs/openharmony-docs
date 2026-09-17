# getSimStateSync

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getSimStateSync

```TypeScript
function getSimStateSync(slotId: number): SimState
```

Obtains the state of the SIM card in the specified slot.

**Since:** 10

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| [SimState](arkts-telephony-sim-simstate-e.md) | State of the SIM card in the specified slot. |

**Examples**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let simState: sim.SimState = sim.getSimStateSync(0);
console.info(`The sim state is:` + simState);
```
