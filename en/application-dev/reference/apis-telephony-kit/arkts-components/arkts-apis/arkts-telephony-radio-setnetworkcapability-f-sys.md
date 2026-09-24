# setNetworkCapability (System API)

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## setNetworkCapability

```TypeScript
function setNetworkCapability(slotId: number, type: NetworkCapabilityType, state: NetworkCapabilityState,
    callback: AsyncCallback<void>): void
```

Set the type and state for the specified network capability.

**Since:** 10

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| type | [NetworkCapabilityType](arkts-telephony-radio-networkcapabilitytype-e-sys.md) | Yes | Indicates the service type of the [NetworkCapabilityType](arkts-telephony-radio-networkcapabilitytype-e-sys.md). |
| state | [NetworkCapabilityState](arkts-telephony-radio-networkcapabilitystate-e-sys.md) | Yes | Indicates the service ability state of the [NetworkCapabilityState](arkts-telephony-radio-networkcapabilitystate-e-sys.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of setNetworkCapability. |

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
let type: radio.NetworkCapabilityType = radio.NetworkCapabilityType.SERVICE_TYPE_NR;
let state: radio.NetworkCapabilityState = radio.NetworkCapabilityState.SERVICE_CAPABILITY_ON;
radio.setNetworkCapability(slotId, type, state, (err: BusinessError) => {
    if (err) {
        console.error(`setNetworkCapability failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`setNetworkCapability success.`);
});
```


<a id="setnetworkcapability-1"></a>

## setNetworkCapability

```TypeScript
function setNetworkCapability(slotId: number, type: NetworkCapabilityType, state: NetworkCapabilityState): Promise<void>
```

Set the type and state for the specified network capability.

**Since:** 10

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| type | [NetworkCapabilityType](arkts-telephony-radio-networkcapabilitytype-e-sys.md) | Yes | Indicates the service type of the [NetworkCapabilityType](arkts-telephony-radio-networkcapabilitytype-e-sys.md). |
| state | [NetworkCapabilityState](arkts-telephony-radio-networkcapabilitystate-e-sys.md) | Yes | Indicates the service ability state of the [NetworkCapabilityState](arkts-telephony-radio-networkcapabilitystate-e-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the setNetworkCapability. |

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
let type: radio.NetworkCapabilityType = radio.NetworkCapabilityType.SERVICE_TYPE_NR;
let state: radio.NetworkCapabilityState = radio.NetworkCapabilityState.SERVICE_CAPABILITY_ON;
radio.setNetworkCapability(slotId, type, state).then(() => {
    console.info(`setNetworkCapability success`);
}).catch((err: BusinessError) => {
    console.error(`setNetworkCapability failed, promise: err->${JSON.stringify(err)}`);
});
```
