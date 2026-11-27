# Interface (WhiteBalance)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=8d7cd89856e59b2dafac0971679b7b6d2f7e5220 translatedAt=2026-11-18T03:36:29.278Z pushedAt=2026-11-20T07:31:16.848Z nl=1 -->

**WhiteBalance** inherits from [WhiteBalanceQuery](arkts-apis-camera-WhiteBalanceQuery.md).

It provides APIs to process white balance, including obtaining and setting the white balance mode and white balance value.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 20.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## setWhiteBalanceMode<sup>20+</sup>

setWhiteBalanceMode(mode: WhiteBalanceMode): void

Sets a white balance mode. Before the setting, run [isWhiteBalanceModeSupported](arkts-apis-camera-WhiteBalanceQuery.md#iswhitebalancemodesupported20) to check whether the device supports the specified white balance mode.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Name     | Type                                     | Mandatory| Description                   |
| -------- |-----------------------------------------| ---- | ----------------------- |
| mode   | [WhiteBalanceMode](arkts-apis-camera-e.md#whitebalancemode20) | Yes  | White balance mode.               |

**Error codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID        | Error Message       |
| --------------- | --------------- |
| 7400101                |  Parameter missing or parameter type incorrect.        |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setWhiteBalanceMode(session: camera.PhotoSession | camera.VideoSession): void {
  try {
    if (session.isWhiteBalanceModeSupported(camera.WhiteBalanceMode.DAYLIGHT)) {
      session.setWhiteBalanceMode(camera.WhiteBalanceMode.DAYLIGHT);
    }
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The setWhiteBalanceMode call failed. error code: ${err.code}`);
  }
}
```

## getWhiteBalanceMode<sup>20+</sup>

getWhiteBalanceMode(): WhiteBalanceMode

Obtains the white balance mode in use.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Return value**

| Type                                     | Description                         |
|-----------------------------------------| ----------------------------- |
| [WhiteBalanceMode](arkts-apis-camera-e.md#whitebalancemode20) | White balance mode in use. If the API call fails, undefined is returned.|

**Error codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID        | Error Message       |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getWhiteBalanceMode(session: camera.PhotoSession | camera.VideoSession): camera.WhiteBalanceMode | undefined {
  let whiteBalanceMode: camera.WhiteBalanceMode | undefined = undefined;
  try {
    whiteBalanceMode = session.getWhiteBalanceMode();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getWhiteBalanceMode call failed. error code: ${err.code}`);
  }
  return whiteBalanceMode;
}
```

## setWhiteBalance<sup>20+</sup>

setWhiteBalance(whiteBalance: number): void

Sets a white balance value.

Before the setting, run [getWhiteBalanceRange](arkts-apis-camera-WhiteBalanceQuery.md#getwhitebalancerange20) to check the white balance value range supported by the device.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Name     | Type                    | Mandatory| Description                |
| -------- | ----------------------- | ---- | ------------------- |
| whiteBalance | number | Yes | White balance value, in units of K (Kelvin). |

**Error codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID        | Error Message       |
| --------------- | --------------- |
| 7400101                |  Parameter missing or parameter type incorrect.        |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setWhiteBalance(session: camera.PhotoSession | camera.VideoSession, whiteBalance: number): void {
  try {
    let whiteBalances: Array<number> = session.getWhiteBalanceRange();
    if (whiteBalance >= whiteBalances[0] && whiteBalance <= whiteBalances[1]) {
      session.setWhiteBalance(whiteBalance);
    } else {
      console.error(`invalid whiteBalance.`);
    }
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The setWhiteBalance call failed. error code: ${err.code}`);
  }
}
```

## getWhiteBalance<sup>20+</sup>

getWhiteBalance(): number

Obtains the current white balance value.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Return value**

| Type       | Description                         |
| ---------- | ----------------------------- |
| number    | White balance value, in units of K (Kelvin). |

**Error codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID        | Error Message       |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getWhiteBalance(session: camera.PhotoSession | camera.VideoSession): number {
  let whiteBalance: number = 0;
  try {
    whiteBalance = session.getWhiteBalance();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getWhiteBalance call failed. error code: ${err.code}`);
  }
  return whiteBalance;
}
```

## setColorTint

setColorTint(colorTint: number): void

Sets the white balance hue adjustment.

Before the setting, run [getColorTintRange](arkts-apis-camera-WhiteBalanceQuery.md#getcolortintrange) to check whether the device supports the specified white balance hue adjustment range.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Name      | Type                     | Mandatory | Description                 |
| -------- | ----------------------- | ---- | ------------------- |
| colorTint | number | Yes   | White balance hue adjustment value. |

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID         | Error Message        |
| --------------- | --------------- |
| 7400103                | Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setColorTint(session: camera.PhotoSession | camera.VideoSession, colorTint: number): void {
  try {
    let tints: Array<number> = session.getColorTintRange();
    if (colorTint >= tints[0] && colorTint <= tints[1]) {
      session.setColorTint(colorTint);
    } else {
      console.error(`invalid colorTint.`);
    }
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The setColorTint call failed. error code: ${err.code}`);
  }
}
```

## getColorTint

getColorTint(): number

Obtains the white balance hue adjustment.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Return value**

| Type        | Description                          |
| ---------- | ----------------------------- |
| number    | White balance hue adjustment value. |

**Error Codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID         | Error Message        |
| --------------- | --------------- |
| 7400103                | Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getColorTint(session: camera.PhotoSession | camera.VideoSession): number {
  let colorTint: number = 0;
  try {
    colorTint = session.getColorTint();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getColorTint call failed. error code: ${err.code}`);
  }
  return colorTint;
}
```