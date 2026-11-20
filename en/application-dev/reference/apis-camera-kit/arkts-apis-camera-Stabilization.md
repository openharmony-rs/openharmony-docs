# Interface (Stabilization)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=fefd645189e794d80ae9ee3e4a15dff8502cd619 translatedAt=2026-11-18T03:34:07.390Z pushedAt=2026-11-20T07:28:08.459Z nl=1 -->

**Stabilization** inherits from [StabilizationQuery](arkts-apis-camera-StabilizationQuery.md).

It provides APIs to set video stabilization.

You can set video stabilization only when a [VideoOutput](arkts-apis-camera-VideoOutput.md) stream exists in the session.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 11.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## getActiveVideoStabilizationMode<sup>11+</sup>

getActiveVideoStabilizationMode(): VideoStabilizationMode

Obtains the video stabilization mode in use.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Return value**

| Type       | Description         |
| ---------- |-------------|
| [VideoStabilizationMode](arkts-apis-camera-e.md#videostabilizationmode)    | Video stabilization mode obtained. If the API call fails, undefined is returned.|

**Error codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID        | Error Message       |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getActiveVideoStabilizationMode(videoSession: camera.VideoSession): camera.VideoStabilizationMode | undefined {
  let vsMode: camera.VideoStabilizationMode | undefined = undefined;
  try {
    vsMode = videoSession.getActiveVideoStabilizationMode();
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The getActiveVideoStabilizationMode call failed. error code: ${err.code}`);
  }
  return vsMode;
}
```

## setVideoStabilizationMode<sup>11+</sup>

setVideoStabilizationMode(mode: VideoStabilizationMode): void

Sets a video stabilization mode. Before the setting, call [isVideoStabilizationModeSupported](arkts-apis-camera-StabilizationQuery.md#isvideostabilizationmodesupported11) to check whether the target video stabilization mode is supported. It is recommended that you set the video stabilization mode between [commitConfig](arkts-apis-camera-Session.md#commitconfig11-1) and [Start](arkts-apis-camera-Session.md#start11-1).

> **NOTE**
>
> Since API version 12, after the HIGH video stabilization mode is set through this API, to ensure video stabilization performance in multiple scenarios, when [getActiveVideoStabilizationMode](#getactivevideostabilizationmode11) is called to query the video stabilization mode currently in use, the result returned is the AUTO mode, that is, the stabilization algorithm is automatically selected.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Name     | Type                                             | Mandatory| Description                   |
| -------- | ------------------------------------------------- | ---- | --------------------- |
| mode     | [VideoStabilizationMode](arkts-apis-camera-e.md#videostabilizationmode) | Yes  | Video stabilization mode.  |

**Error codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID        | Error Message       |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setVideoStabilizationMode(videoSession: camera.VideoSession): void {
  try {
    if (videoSession.isVideoStabilizationModeSupported(camera.VideoStabilizationMode.OFF)) {
      videoSession.setVideoStabilizationMode(camera.VideoStabilizationMode.OFF);
    }
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The setVideoStabilizationMode call failed. error code: ${err.code}`);
  }
}
```
