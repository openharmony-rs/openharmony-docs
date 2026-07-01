# Interface (Aperture)

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=df2388ac9ece670e2be6918a776640e250f776ef translatedAt=2026-06-25T02:36:09.254Z pushedAt=2026-06-25T06:57:19.543Z -->

**Aperture** inherits from [ApertureQuery](arkts-apis-camera-ApertureQuery.md).

Describes a physical aperture object.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 24.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## getPhysicalAperture<sup>24+</sup>

getPhysicalAperture(): number

Obtains the physical aperture in use.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Returns**

| Type       | Description                         |
| ---------- | ----------------------------- |
| number    | Physical aperture in use.|

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getPhysicalAperture(photoSession: camera.PhotoSession): number {
  let aperture = 0.0;
  try {
    aperture = photoSession.getPhysicalAperture();
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The getPhysicalAperture call failed. error code: ${err.code}`);
  }
  return aperture;
}
```

## setPhysicalAperture<sup>24+</sup>

setPhysicalAperture(aperture: number): void

Sets a physical aperture. Obtain the aperture values that can be set at different focal lengths using [getSupportedPhysicalApertures](arkts-apis-camera-ApertureQuery.md#getsupportedphysicalapertures24), and then set a supported physical aperture by adjusting the focal length range.

For example, the physical aperture can be set to **2.6** when **zoomRange** is within the range of [1, 4]. Therefore, you need to set the focal length to be within the range of [1, 4] using [setZoomRatio](arkts-apis-camera-Zoom.md#setzoomratio11) in order to set the physical aperture value to **2.6**.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Name     | Type                          | Mandatory | Description                          |
| -------- | -------------------------------| ---- | ----------------------------- |
| aperture   | number  | Yes  | Physical aperture.                |

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setPhysicalAperture(photoSession: camera.PhotoSession, aperture: number): void {
  try {
    photoSession.setPhysicalAperture(aperture);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The setPhysicalAperture call failed. error code: ${err.code}`);
  }
}
```