# getSignalInformationSync

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## getSignalInformationSync

```TypeScript
function getSignalInformationSync(slotId: number): Array<SignalInformation>
```

Obtains a list of signal strengths of the network with which the SIM card in the specified slot is registered.

**Since:** 10

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[SignalInformation](arkts-telephony-radio-signalinformation-i.md)&gt; | Array of child class objects derived from [SignalInformation](arkts-telephony-radio-signalinformation-i.md). |

**Examples**

```TypeScript
let slotId: number = 0;
let signalInfo: Array<radio.SignalInformation> = radio.getSignalInformationSync(slotId);
console.info(`signal information size is:` + signalInfo.length);
```
