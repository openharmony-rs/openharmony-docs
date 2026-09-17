# controlCamera (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## controlCamera

```TypeScript
function controlCamera(callId: number, cameraId: string): Promise<void>
```

Uses the specified camera to make a video call. If **cameraId** is left empty, the camera is disabled. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callId | number | Yes | Call ID. You can obtain the value by subscribing to **callDetailsChange** events. |
| cameraId | string | Yes | Camera ID. For details about how to obtain the camera ID, see the [getSupportedCameras](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameramanager-i.md#getsupportedcameras) API in camera management. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result of starting, closing, or switching a camera. |

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

call.controlCamera(1, "1").then(() => {
    console.info(`controlCamera success.`);
}).catch((err: BusinessError) => {
    console.error(`controlCamera fail, promise: err->${JSON.stringify(err)}`);
});
```
