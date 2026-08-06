# Interface (ManualExposure)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

**ManualExposure** inherits from [ManualExposureQuery](arkts-apis-camera-ManualExposureQuery.md).

Describes a manual exposure object.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 24.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## getExposureDuration<sup>24+</sup>

getExposureDuration(): number

Obtains the exposure duration.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Returns**

| Type       | Description                         |
| ---------- | ----------------------------- |
| number    | Exposure duration, in microseconds.|

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID        | Error Message       |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, session or inputdevice maybe abnormal.                                   |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getExposureDuration(photoSession: camera.PhotoSession): number {
  let exposureDuration: number = 0;
  try {
    exposureDuration = photoSession.getExposureDuration();
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The getExposureDuration call failed. error code: ${err.code}`);
  }
  return exposureDuration;
}
```

## setExposureDuration<sup>24+</sup>

setExposureDuration(exposureDuration: number): void

Sets the exposure duration.

The setting takes effect only when [ExposureMode](arkts-apis-camera-e.md#exposuremode) is set to **EXPOSURE_MODE_MANUAL**.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Parameter     | Type                          | Mandatory | Description                          |
| -------- | -------------------------------| ---- | ----------------------------- |
| exposureDuration   | number  | Yes  | Exposure duration, in microseconds.                |

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID        | Error Message       |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setExposureDuration(photoSession: camera.PhotoSession, exposureDuration: number): void {
  try {
    photoSession.setExposureDuration(exposureDuration);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The setExposureDuration call failed. error code: ${err.code}`);
  }
}
```

## onExposureInfoChange<sup>24+</sup>

onExposureInfoChange(callback: Callback\<ExposureInfo\>): void

Subscribes to exposure information change events. After the exposure parameters are modified, the system returns the updated exposure information.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Parameter    | Type           | Mandatory| Description      |
| -------- | -----------------| ---- | --------- |
| callback | Callback\<[ExposureInfo](arkts-apis-camera-i.md#exposureinfo24)\> | Yes  | Callback used to obtain the exposure information.|

**Example**

```ts
function onExposureInfoChange(photoSession: camera.PhotoSession): void {
  photoSession.onExposureInfoChange((exposureInfo: camera.ExposureInfo) => {
    console.info(`Exposure info changed, exposureTime: ${exposureInfo.exposureTime}`);
  });
}
```

## offExposureInfoChange<sup>24+</sup>

offExposureInfoChange(callback?: Callback\<ExposureInfo\>): void

Unsubscribes from exposure information change events. If you have subscribed to exposure information change events, cancel the subscription before releasing the camera object.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Parameter    | Type           | Mandatory| Description      |
| -------- | -----------------| ---- | --------- |
| callback | Callback\<[ExposureInfo](arkts-apis-camera-i.md#exposureinfo24)\> | No  | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled.|

**Example**

```ts
function offExposureInfoChange(photoSession: camera.PhotoSession): void {
  photoSession.offExposureInfoChange();
}
```
