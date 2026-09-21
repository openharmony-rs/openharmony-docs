# setShowNumber (System API)

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## setShowNumber

```TypeScript
function setShowNumber(slotId: number, teleNumber: string, callback: AsyncCallback<void>): void
```

Set the SIM card number in the specified slot.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| teleNumber | string | Yes | Indicates SIM card number. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of setShowNumber. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

let number: string = '+861xxxxxxxxxx';
sim.setShowNumber(0, number, (err: BusinessError) => {
    console.info(`callback: err->${JSON.stringify(err)}`);
});
```


<a id="setshownumber-1"></a>

## setShowNumber

```TypeScript
function setShowNumber(slotId: number, teleNumber: string): Promise<void>
```

Set the SIM card number in the specified slot.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| teleNumber | string | Yes | Indicates SIM card number. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the setShowNumber. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

let number: string = '+861xxxxxxxxxx';
sim.setShowNumber(0, number).then(() => {
    console.info(`setShowNumber success.`);
}).catch((err: BusinessError) => {
    console.error(`setShowNumber failed, promise: err->${JSON.stringify(err)}`);
});
```
