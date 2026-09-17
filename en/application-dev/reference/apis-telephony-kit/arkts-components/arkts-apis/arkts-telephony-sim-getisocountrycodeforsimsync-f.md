# getISOCountryCodeForSimSync

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getISOCountryCodeForSimSync

```TypeScript
function getISOCountryCodeForSimSync(slotId: number): string
```

Obtains the ISO country code of the SIM card in the specified slot.

**Since:** 10

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| string | ISO country code of the SIM card in the specified slot, for example, **CN** (China). |

**Examples**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let countryCode: string = sim.getISOCountryCodeForSimSync(0);
console.info(`the country ISO is:` + countryCode);
```
