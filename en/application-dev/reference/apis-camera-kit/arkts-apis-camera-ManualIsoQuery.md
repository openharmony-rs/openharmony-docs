# Interface (ManualIsoQuery)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Describes a manual ISO query object.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 24.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## getSupportedIsoRange<sup>24+</sup>

getSupportedIsoRange(): number[]

Obtains the supported ISO range.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Returns**

| Type       | Description                         |
| ---------- | ----------------------------- |
| number[]    | ISO range.|

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400102 | Operation not allowed, the inputDevice or the session is abnormal. |
| 7400103 | Session not config, only throw in session usage. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getSupportedIsoRange(photoSession: camera.PhotoSession): number[] {
  let isoRange: number[] = [];
  try {
    isoRange = photoSession.getSupportedIsoRange();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getSupportedIsoRange call failed. error code: ${err.code}`);
  }
  return isoRange;
}
```
