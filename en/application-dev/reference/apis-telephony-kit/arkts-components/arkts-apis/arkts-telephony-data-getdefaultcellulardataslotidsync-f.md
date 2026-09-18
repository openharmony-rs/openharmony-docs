# getDefaultCellularDataSlotIdSync

## Modules to Import

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## getDefaultCellularDataSlotIdSync

```TypeScript
function getDefaultCellularDataSlotIdSync(): number
```

Obtains the default SIM card used for mobile data synchronously.

**Since:** 9

**System capability:** SystemCapability.Telephony.CellularData

**Return value:**

| Type | Description |
| --- | --- |
| number | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 <br>- **2**: slot ID of the mobile data in the eSIM and SkyTone scenarios. |

**Examples**

```TypeScript
import { data } from '@kit.TelephonyKit';

console.info("Result: "+ data.getDefaultCellularDataSlotIdSync())
```
