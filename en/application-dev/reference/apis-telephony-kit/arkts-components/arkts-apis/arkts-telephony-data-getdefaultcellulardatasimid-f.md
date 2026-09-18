# getDefaultCellularDataSimId

## Modules to Import

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## getDefaultCellularDataSimId

```TypeScript
function getDefaultCellularDataSimId(): number
```

Obtains the default ID of the SIM card used for mobile data.

**Since:** 10

**System capability:** SystemCapability.Telephony.CellularData

**Return value:**

| Type | Description |
| --- | --- |
| number | Obtains the default ID of the SIM card used for mobile data.<br>The return value is bound to the SIM card and increases from 1. <br>- **0**: no SIM card. <br>- **9999**: ID of the SIM card used for mobile data in the eSIM scenario. <br>- **99999**: ID of the SIM card used for mobile data in the SkyTone scenario. The default value is **99999**. |

**Examples**

```TypeScript
import { data } from '@kit.TelephonyKit';

console.info("Result: "+ data.getDefaultCellularDataSimId());
```
