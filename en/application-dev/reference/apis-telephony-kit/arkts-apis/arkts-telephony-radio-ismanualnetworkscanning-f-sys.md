# isManualNetworkScanning (System API)

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## isManualNetworkScanning

```TypeScript
function isManualNetworkScanning(slotId: number): Promise<boolean>
```

Determine whether the current manual network scan is in progress.

**Since:** 23

**Required permissions:** ohos.permission.GET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | the promise return ManualNetworkScanState. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Nonsystem applications use system APIs. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

```TypeScript
radio.isManualNetworkScanning(0).then((state: boolean) => {
    console.info(`isManualNetworkScanning success, state->${JSON.stringify(state)}`);
}).catch((err: BusinessError) => {
    console.error(`isManualNetworkScanning failed, promise: err->${JSON.stringify(err)}`);
});
```
