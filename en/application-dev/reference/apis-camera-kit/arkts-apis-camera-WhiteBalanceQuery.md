# Interface (WhiteBalanceQuery)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

WhiteBalanceQuery provides APIs to check whether a white balance mode is supported and obtain the white balance mode range supported.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 20.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## isWhiteBalanceModeSupported<sup>20+</sup>

isWhiteBalanceModeSupported(mode: WhiteBalanceMode): boolean

Checks whether a white balance mode is supported.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Name     | Type                                     | Mandatory | Description                          |
| -------- |-----------------------------------------| ---- | ----------------------------- |
| mode   | [WhiteBalanceMode](arkts-apis-camera-e.md#whitebalancemode20) | Yes  | White balance mode.                     |

**Return value**

| Type       | Description                         |
| ---------- | ----------------------------- |
| boolean    | Check result for the support of the white balance mode. **true** if supported, **false** otherwise. If the API call fails, undefined is returned.|

**Error codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400101                |  Parameter missing or parameter type incorrect.        |
| 7400103                |  Session not config, only throw in session usage.                                  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function isWhiteBalanceModeSupported(session: camera.PhotoSession | camera.VideoSession): boolean {
  let status: boolean = false;
  try {
  let mode: camera.WhiteBalanceMode = camera.WhiteBalanceMode.DAYLIGHT;
    status = session.isWhiteBalanceModeSupported(mode);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The isWhiteBalanceModeSupported call failed. error code: ${err.code}`);
  }
  return status;
}
```

## getWhiteBalanceRange<sup>20+</sup>

getWhiteBalanceRange(): Array\<number\>

Obtains the range of white balance values in manual white balance mode.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Return value**

| Type       | Description                         |
| ---------- | ----------------------------- |
| Array\<number\>   | Range of white balance values, for example, [2800, ...,10000], in units of K (Kelvin). The actual value depends on the bottom-layer capability. If the API call fails, undefined is returned.|

**Error codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400103                |  Session not config, only throw in session usage.                                  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getWhiteBalanceRange(session: camera.PhotoSession | camera.VideoSession): Array<number> {
  let range: Array<number> = [];
  try {
    range = session.getWhiteBalanceRange();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getWhiteBalanceRange call failed. error code: ${err.code}`);
  }
  return range;
}
```

## getColorTintRange

getColorTintRange(): Array\<number\>

Obtains the supported white balance hue adjustment range.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Return value**

| Type       | Description                         |
| ---------- | ----------------------------- |
| Array\<number\>   | Hue adjustment range. If the API call fails, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code        | Error Message       |
| --------------- | --------------- |
| 7400103                |  Session not config, only throw in session usage.                                  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getColorTintRange(session: camera.PhotoSession | camera.VideoSession): Array<number> {
  let range: Array<number> = [];
  try {
    range = session.getColorTintRange();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getColorTintRange call failed. error code: ${err.code}`);
  }
  return range;
}
```
