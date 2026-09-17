# setDeviceDirection (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## setDeviceDirection

```TypeScript
function setDeviceDirection(callId: number, deviceDirection: DeviceDirection): Promise<void>
```

Sets the video call screen to follow the device direction. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callId | number | Yes | Call ID. You can obtain the value by subscribing to **callDetailsChange** events. |
| deviceDirection | [DeviceDirection](arkts-telephony-call-devicedirection-e-sys.md) | Yes | Device direction. It determines the direction of the video call screen. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.setDeviceDirection(1, 0).then(() => {
    console.info(`setDeviceDirection success.`);
}).catch((err: BusinessError) => {
    console.error(`setDeviceDirection fail, promise: err->${JSON.stringify(err)}`);
});
```
