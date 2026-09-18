# getISOCountryCodeForNetworkSync

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## getISOCountryCodeForNetworkSync

```TypeScript
function getISOCountryCodeForNetworkSync(slotId: number): string
```

Obtains the ISO country code of the network with which the SIM card in the specified slot is registered.

**Since:** 10

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| string | ISO country code of the network, for example, **CN** (China). If the device is not registered with any network, an empty string is returned. |

**Examples**

```TypeScript
let slotId: number = 0;
let countryISO: string = radio.getISOCountryCodeForNetworkSync(slotId);
console.info(`the country ISO is:` + countryISO);
```
