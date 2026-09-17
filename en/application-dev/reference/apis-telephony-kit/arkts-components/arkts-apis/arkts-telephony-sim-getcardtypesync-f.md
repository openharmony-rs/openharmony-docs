# getCardTypeSync

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getCardTypeSync

```TypeScript
function getCardTypeSync(slotId: number): CardType
```

Obtains the type of the SIM card in the specified slot.

**Since:** 10

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| [CardType](arkts-telephony-sim-cardtype-e.md) | Type of the SIM card in the specified slot. |

**Examples**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let cardType: sim.CardType = sim.getCardTypeSync(0);
console.info(`the card type is:` + cardType);
```
