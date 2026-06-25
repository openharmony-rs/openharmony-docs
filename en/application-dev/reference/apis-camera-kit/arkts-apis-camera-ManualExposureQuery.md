# APIs (ManualExposureQuery)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Describes a manual exposure query object.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 24.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## getSupportedExposureDurationRange<sup>24+</sup>

getSupportedExposureDurationRange(): Array\<number\>

Obtains the supported manual exposure durations, in microseconds.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value**

| Type       | Description                         |
| ---------- | ----------------------------- |
| Array\<number\>    | Array of manual exposure durations supported.|

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400102 | Operation not allowed, session or inputdevice maybe abnormal. |
| 7400103 | Session not config, only throw in session usage. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getSupportedExposureDurationRange(photoSession: camera.PhotoSession): Array<number> {
  let durationRange: Array<number> = [];
  try {
    durationRange = photoSession.getSupportedExposureDurationRange();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getSupportedExposureDurationRange call failed. error code: ${err.code}`);
  }
  return durationRange;
}
```

## getExposureBiasStep<sup>24+</sup>

getExposureBiasStep(): number

Obtains the exposure bias step.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value**

| Type       | Description                         |
| ---------- | ----------------------------- |
| number    | Exposure bias step.|

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400102 | Operation not allowed, session or inputdevice maybe abnormal. |
| 7400103 | Session not config. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getExposureBiasStep(photoSession: camera.PhotoSession): number {
  let biasStep = 0.0;
  try {
    biasStep = photoSession.getExposureBiasStep();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getExposureBiasStep call failed. error code: ${err.code}`);
  }
  return biasStep;
}
```
