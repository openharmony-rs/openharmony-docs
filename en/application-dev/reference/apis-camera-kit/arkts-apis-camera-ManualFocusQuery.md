# Interface (ManualFocusQuery)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Describes a manual focus query object.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 24.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## isFocusDistanceSupported<sup>24+</sup>

isFocusDistanceSupported(): boolean

Checks whether the focus distance can be set.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Returns**

| Type       | Description                         |
| ---------- | ----------------------------- |
| boolean    | Whether focus distance setting is supported. The value **true** indicates that focus distance setting is supported, and the value **false** indicates the opposite.|

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400103 | Session not config, only throw in session usage. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function isFocusDistanceSupported(photoSession: camera.PhotoSession): boolean {
  let isSupported = false;
  try {
    isSupported = photoSession.isFocusDistanceSupported();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The isFocusDistanceSupported call failed. error code: ${err.code}`);
  }
  return isSupported;
}
```
