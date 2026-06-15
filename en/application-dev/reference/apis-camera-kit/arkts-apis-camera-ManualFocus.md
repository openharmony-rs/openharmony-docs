# Interface (ManualFocus)

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=417fc360382b810eaca71d157c09ed3f2422bbbb translatedAt=2026-06-10T02:10:36.974Z pushedAt=2026-06-10T05:56:30.865Z -->

**ManualFocus** inherits from [ManualFocusQuery](arkts-apis-camera-ManualFocusQuery.md).

Describes a manual focus object.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 24.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## getFocusDistance<sup>24+</sup>

getFocusDistance(): number

Obtains the focus distance, in the range [0.0, 1.0], where **0.0** indicates the shortest achievable focus distance and **1.0** indicates the longest focus distance. The default value is **1.0**.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Returns**

| Type       | Description                         |
| ---------- | ----------------------------- |
| number    | Current focus distance, in the range [0.0, 1.0].|

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getFocusDistance(photoSession: camera.PhotoSession): number {
  let focusDistance = 1.0;
  try {
    focusDistance = photoSession.getFocusDistance();
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The getFocusDistance call failed. error code: ${err.code}`);
  }
  return focusDistance;
}
```

## setFocusDistance<sup>24+</sup>

setFocusDistance(distance: number): void

Sets the focus distance, in the range [0.0, 1.0], where **0.0** indicates the shortest achievable focus distance and **1.0** indicates the longest focus distance. The default value is **1.0**. If the value of the input parameter is out of range, the nearest boundary value is used.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Parameter     | Type                          | Mandatory | Description                          |
| -------- | -------------------------------| ---- | ----------------------------- |
| distance   | number  | Yes  | Focus distance, in the range [0.0, 1.0].                |

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setFocusDistance(photoSession: camera.PhotoSession, distance: number): void {
  try {
    photoSession.setFocusDistance(distance);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The setFocusDistance call failed. error code: ${err.code}`);
  }
}
```