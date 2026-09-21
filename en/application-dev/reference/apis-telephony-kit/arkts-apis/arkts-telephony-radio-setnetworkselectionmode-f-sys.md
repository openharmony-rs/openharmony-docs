# setNetworkSelectionMode (System API)

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## setNetworkSelectionMode

```TypeScript
function setNetworkSelectionMode(options: NetworkSelectionModeOptions, callback: AsyncCallback<void>): void
```

Set the current network selection mode.

**Since:** 6

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [NetworkSelectionModeOptions](arkts-telephony-radio-networkselectionmodeoptions-i-sys.md) | Yes | Indicates the network selection mode option. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of setNetworkSelectionMode. |

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

let networkInformation: radio.NetworkInformation = {
    operatorName: "China Mobile",
    operatorNumeric: "898600",
    state: radio.NetworkInformationState.NETWORK_AVAILABLE,
    radioTech: "CS"
}
let networkSelectionModeOptions: radio.NetworkSelectionModeOptions = {
    slotId: 0,
    selectMode: radio.NetworkSelectionMode.NETWORK_SELECTION_AUTOMATIC,
    networkInformation: networkInformation,
    resumeSelection: true
}
radio.setNetworkSelectionMode(networkSelectionModeOptions, (err: BusinessError) => {
    if (err) {
        console.error(`setNetworkSelectionMode failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`setNetworkSelectionMode success.`);
});
```


<a id="setnetworkselectionmode-1"></a>

## setNetworkSelectionMode

```TypeScript
function setNetworkSelectionMode(options: NetworkSelectionModeOptions): Promise<void>
```

Set the current network selection mode.

**Since:** 6

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [NetworkSelectionModeOptions](arkts-telephony-radio-networkselectionmodeoptions-i-sys.md) | Yes | Indicates the network selection mode option. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the setNetworkSelectionMode. |

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

let networkInformation: radio.NetworkInformation = {
    operatorName: "China Mobile",
    operatorNumeric: "898600",
    state: radio.NetworkInformationState.NETWORK_AVAILABLE,
    radioTech: "CS"
}
let networkSelectionModeOptions: radio.NetworkSelectionModeOptions = {
    slotId: 0,
    selectMode: radio.NetworkSelectionMode.NETWORK_SELECTION_AUTOMATIC,
    networkInformation: networkInformation,
    resumeSelection: true
}
radio.setNetworkSelectionMode(networkSelectionModeOptions).then(() => {
    console.info(`setNetworkSelectionMode success.`);
}).catch((err: BusinessError) => {
    console.error(`setNetworkSelectionMode failed, promise: err->${JSON.stringify(err)}`);
});
```
