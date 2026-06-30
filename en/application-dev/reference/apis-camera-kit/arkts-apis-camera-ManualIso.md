# Interface (ManualIso)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

**ManualIso** inherits from [ManualIsoQuery](arkts-apis-camera-ManualIsoQuery.md).

Describes a manual ISO object.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 24.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## getIso<sup>24+</sup>

getIso(): number

Obtains the ISO value.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Returns**

| Type       | Description                         |
| ---------- | ----------------------------- |
| number    | ISO value.|

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID        | Error Message       |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getIso(photoSession: camera.PhotoSession): number {
  let iso: number = 0;
  try {
    iso = photoSession.getIso();
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The getIso call failed. error code: ${err.code}`);
  }
  return iso;
}
```

## setIso<sup>24+</sup>

setIso(iso: number): void

Sets the ISO sensitivity or ISO speed. The setting is supported only when [ExposureMode](arkts-apis-camera-e.md#exposuremode) is set to **EXPOSURE_MODE_LOCKED**. The value must be within the range specified by [getSupportedIsoRange](arkts-apis-camera-ManualIsoQuery.md#getsupportedisorange24).

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Parameter     | Type                          | Mandatory | Description                          |
| -------- | -------------------------------| ---- | ----------------------------- |
| iso   | number  | Yes  | ISO sensitivity or ISO speed.                |

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID        | Error Message       |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config.                                   |


**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setIso(photoSession: camera.PhotoSession, iso: number): void {
  try {
    photoSession.setIso(iso);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The setIso call failed. error code: ${err.code}`);
  }
}
```
