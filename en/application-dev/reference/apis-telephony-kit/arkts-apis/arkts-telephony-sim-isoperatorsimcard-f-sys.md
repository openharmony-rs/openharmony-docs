# isOperatorSimCard (System API)

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## isOperatorSimCard

```TypeScript
function isOperatorSimCard(slotId: number, operator: OperatorSimCard): boolean
```

This API is used to check whether the SIM card in a specified card slot is a SIM card of a specified carrier. For example, a carrier-dedicated app can use this interface to determine whether the current SIM card is a carrier-dedicated app and determine whether to display carrier-dedicated services or functions.

**Since:** 11

<!--Device-sim-function isOperatorSimCard(slotId: int, operator: OperatorSimCard): boolean--><!--Device-sim-function isOperatorSimCard(slotId: int, operator: OperatorSimCard): boolean-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID. <br>- 0: card slot 1<br>- 1: card slot 2. <br>The value should be an integer. |
| operator | [OperatorSimCard](arkts-telephony-sim-operatorsimcard-e-sys.md) | Yes | Carrier card name. (Currently, only China Telecom cards are supported.). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns whether the specified card slot is a specified carrier card. <br>- true: yes <br>- false: no |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.         2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

<!--Del-->
**Examples**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let slotId : number = 0;
let operator : sim.OperatorSimCard = sim.OperatorSimCard.CHINA_TELECOM_CARD;
try {
    let isOperatorSimCard: boolean = sim.isOperatorSimCard(slotId, operator);
    console.info(`is operator sim card: ` + isOperatorSimCard);
} catch (err) {
    console.error("isOperatorSimCard err: " + JSON.stringify(err));
}
```

<!--DelEnd-->
