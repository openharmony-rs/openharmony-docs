# Interface (OIS)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

**OIS** inherits from [OISQuery](arkts-apis-camera-OISQuery.md).

This module describes the optical image stabilization (OIS) object.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 24.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## setOISMode<sup>24+</sup>

setOISMode(mode: OISMode): void

Sets the OIS mode.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Name    | Type            | Mandatory| Description      |
| -------- | --------------- | ---- | --------- |
| mode | [OISMode](arkts-apis-camera-e.md#oismode24) | Yes| OIS mode.|

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400102 | Operation not allowed, the inputDevice or the session is abnormal. |
| 7400103 | Session not config. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setOISMode(photoSession: camera.PhotoSession, mode: camera.OISMode): void {
  try {
    photoSession.setOISMode(mode);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The setOISMode call failed. error code: ${err.code}`);
  }
}
```

## setOISModeCustom<sup>24+</sup>

setOISModeCustom(pitch: number, yaw: number): void

Sets the OIS offset on each axis. This API can be called only when [OISMode](arkts-apis-camera-e.md#oismode24) is set to **CUSTOM**.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Name    | Type            | Mandatory| Description      |
| -------- | --------------- | ---- | --------- |
| pitch | number | Yes| Offset on the pitch axis.|
| yaw | number | Yes| Offset on the yaw axis.|

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400102 | Operation not allowed, the inputDevice or the session is abnormal. |
| 7400103 | Session not config. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setOISModeCustom(photoSession: camera.PhotoSession, pitch: number, yaw: number): void {
  try {
    photoSession.setOISModeCustom(pitch, yaw);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The setOISModeCustom call failed. error code: ${err.code}`);
  }
}
```
<!--no_check-->
