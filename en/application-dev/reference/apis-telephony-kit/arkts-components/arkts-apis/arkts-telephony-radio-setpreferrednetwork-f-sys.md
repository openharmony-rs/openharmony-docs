# setPreferredNetwork (System API)

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## setPreferredNetwork

```TypeScript
function setPreferredNetwork(slotId: number, networkMode: PreferredNetworkMode, callback: AsyncCallback<void>): void
```

Set the preferred network for the specified SIM card slot.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| networkMode | [PreferredNetworkMode](arkts-telephony-radio-preferrednetworkmode-e-sys.md) | Yes | Indicates that you want to set the preferred network mode. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of setPreferredNetwork. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let mode: radio.PreferredNetworkMode = radio.PreferredNetworkMode.PREFERRED_NETWORK_MODE_GSM;
radio.setPreferredNetwork(slotId, mode, (err: BusinessError) => {
    if (err) {
        console.error(`setPreferredNetwork failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`setPreferredNetwork success.`);
});
```


<a id="setpreferrednetwork-1"></a>

## setPreferredNetwork

```TypeScript
function setPreferredNetwork(slotId: number, networkMode: PreferredNetworkMode): Promise<void>
```

Set the preferred network for the specified SIM card slot.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| networkMode | [PreferredNetworkMode](arkts-telephony-radio-preferrednetworkmode-e-sys.md) | Yes | Indicates that you want to set the preferred network mode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the setPreferredNetwork. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let mode: radio.PreferredNetworkMode = radio.PreferredNetworkMode.PREFERRED_NETWORK_MODE_GSM;
radio.setPreferredNetwork(slotId, mode).then(() => {
    console.info(`setPreferredNetwork success.`);
}).catch((err: BusinessError) => {
    console.error(`setPreferredNetwork failed, promise: err->${JSON.stringify(err)}`);
});
```
