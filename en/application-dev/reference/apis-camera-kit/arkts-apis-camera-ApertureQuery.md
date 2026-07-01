# Interface (ApertureQuery)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Describes a physical aperture query object.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 24.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## getSupportedPhysicalApertures<sup>24+</sup>

getSupportedPhysicalApertures(): Array\<PhysicalAperture\>

Obtains the supported physical apertures.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Returns**

| Type       | Description                         |
| ---------- | ----------------------------- |
| Array\<[PhysicalAperture](arkts-apis-camera-i.md#physicalaperture24)\>     | Array of physical apertures supported.|

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID        | Error Message       |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getSupportedPhysicalApertures(photoSession: camera.PhotoSession): Array<camera.PhysicalAperture> {
  let apertures: Array<camera.PhysicalAperture> = [];
  try {
    apertures = photoSession.getSupportedPhysicalApertures();
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The getSupportedPhysicalApertures call failed. error code: ${err.code}`);
  }
  return apertures;
}
```
