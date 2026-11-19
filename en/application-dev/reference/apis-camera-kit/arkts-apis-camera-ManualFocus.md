# APIs (ManualFocus)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a919c71f7c4adbe3502ca40ecdaaea98656bd2aa translatedAt=2026-11-18T03:31:33.528Z pushedAt=2026-11-19T11:52:37.476Z nl=1 -->

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

Obtains the focus distance in use. The value range is [0.0, 1.0], where **0.0** indicates the shortest achievable focus distance and **1.0** indicates the longest focus distance. The default value is **1.0**.

Before obtaining, [isFocusDistanceSupported](arkts-apis-camera-ManualFocusQuery.md#isfocusdistancesupported24) can be used to check whether setting the focus distance is supported.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value**

| Type       | Description                         |
| ---------- | ----------------------------- |
| number    | Focus distance. The value range is [0.0, 1.0].|

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
    if (photoSession.isFocusDistanceSupported()) {
      focusDistance = photoSession.getFocusDistance();
    }
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

Sets the focus distance. The value range is [0.0, 1.0], where **0.0** indicates the shortest achievable focus distance and **1.0** indicates the longest focus distance. The default value is **1.0**. If the value of the input parameter exceeds the range, the nearest boundary value is used.

Before setting, [isFocusDistanceSupported](arkts-apis-camera-ManualFocusQuery.md#isfocusdistancesupported24) can be used to check whether setting the focus distance is supported.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters**

| Parameter     | Type                          | Mandatory | Description                          |
| -------- | -------------------------------| ---- | ----------------------------- |
| distance   | number  | Yes  | Focus distance The value range is [0.0, 1.0].                |

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
    if (photoSession.isFocusDistanceSupported()) {
      photoSession.setFocusDistance(distance);
    }
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The setFocusDistance call failed. error code: ${err.code}`);
  }
}
```