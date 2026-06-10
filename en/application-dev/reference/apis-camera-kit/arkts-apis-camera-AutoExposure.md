# API (AutoExposure)

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=d0c7a5fb2bc1f1b1c7630c4a5886ec88f6136925 translatedAt=2026-06-09T10:27:40.880Z pushedAt=2026-06-10T01:59:42.625Z -->

**AutoExposure** inherits from [AutoExposureQuery](arkts-apis-camera-AutoExposureQuery.md).

Auto Exposure class, used for device Auto Exposure (AE) operations.

> **NOTE:**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this API are supported since API version 11.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## getExposureMode<sup>11+</sup>

getExposureMode(): ExposureMode

Obtains the current exposure mode.

> **NOTE**
>
> If [setExposureMode](arkts-apis-camera-AutoExposure.md#setexposuremode11) is not called to set the exposure mode, calling this API directly to query the current exposure mode will return an invalid value.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Return value**

| Type        | Description                          |
| ---------- | ----------------------------- |
| [ExposureMode](arkts-apis-camera-e.md#exposuremode)    | Obtains the current exposure mode. If the API call fails, a corresponding error code is thrown and undefined is returned. For details about the error code type, see [CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode). |

**Error codes**

For details about the following error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code         | Error Message        |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getExposureMode(photoSession: camera.PhotoSession): camera.ExposureMode | undefined {
  let exposureMode: camera.ExposureMode | undefined = undefined;
  try {
    exposureMode = photoSession.getExposureMode();
  } catch (error) {
    // If a failure occurs, the error code error.code is returned and handled.
    let err = error as BusinessError;
    console.error(`The getExposureMode call failed. error code: ${err.code}`);
  }
  return exposureMode;
}
```

## setExposureMode<sup>11+</sup>

setExposureMode(aeMode: ExposureMode): void

Sets the exposure mode. Before setting, check whether the device supports the specified exposure mode. You can use [isExposureModeSupported](arkts-apis-camera-AutoExposureQuery.md#isexposuremodesupported11).

**Atomic service API**: This API can be used in atomic services since API version 19.

**System Capability:** SystemCapability.Multimedia.Camera.Core

**Parameters**

| Name      | Type                            | Mandatory | Description                    |
| -------- | -------------------------------| ---- | ----------------------- |
| aeMode   | [ExposureMode](arkts-apis-camera-e.md#exposuremode)  | Yes   | Exposure mode. If the parameter is null or undefined, it is treated as 0, and the exposure is locked.                |

**Error codes**

For details about the following error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code         | Error Message        |
| --------------- | --------------- |
| 7400102                | Operation not allowed.                                 |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setExposureMode(photoSession: camera.PhotoSession): void {
  try {
    photoSession.setExposureMode(camera.ExposureMode.EXPOSURE_MODE_LOCKED);
  } catch (error) {
    // If the operation fails, an error code is returned and error.code is processed.
    let err = error as BusinessError;
    console.error(`The setExposureMode call failed. error code: ${err.code}`);
  }
}
```

## getMeteringPoint<sup>11+</sup>

getMeteringPoint(): Point

Queries the center point of the exposure region.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Return value**

| Type        | Description                          |
| ---------- | ----------------------------- |
| [Point](arkts-apis-camera-i.md#point)    | Obtains the current exposure point. If the API call fails, the corresponding error code will be returned. For details about the error code type, see [CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode). |

**Error codes**

For details about the following error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code   | Error Message        |
|---------| --------------- |
| 7400103 |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getMeteringPoint(photoSession: camera.PhotoSession): camera.Point | undefined {
  let exposurePoint: camera.Point | undefined = undefined;
  try {
    exposurePoint = photoSession.getMeteringPoint();
  } catch (error) {
    // The error code error.code is returned upon failure and should be handled.
    let err = error as BusinessError;
    console.error(`The getMeteringPoint call failed. error code: ${err.code}`);
  }
  return exposurePoint;
}
```

## setMeteringPoint<sup>11+</sup>

setMeteringPoint(point: Point): void

Sets the center point of the exposure region. The exposure point should be within a 0-1 coordinate system, where the top-left corner is {0, 0} and the bottom-right corner is {1, 1}.

The coordinate system is based on the horizontal device direction with the device's charging port on the right. If the layout of the preview screen of an application is based on the vertical direction with the charging port on the lower side, the layout width and height are {w, h}, and the touch point is {x, y}, then the coordinate point after conversion is {y/h, 1-x/w}.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System Capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Parameter Name           | Type                            | Mandatory | Description                 |
| ------------- | -------------------------------| ---- | ------------------- |
| point | [Point](arkts-apis-camera-i.md#point)                | Yes   | Exposure point. The x and y values must be set within the range [0, 1]. If the value exceeds the range, it is set to 0 if less than 0, and 1 if greater than 1.             |

**Error codes**

For details about the following error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code         | Error Message        |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setMeteringPoint(photoSession: camera.PhotoSession): void {
  const point: camera.Point = {x: 1, y: 1};
  try {
    photoSession.setMeteringPoint(point);
  } catch (error) {
    // If the operation fails, an error code is returned and handled.
    let err = error as BusinessError;
    console.error(`The setMeteringPoint call failed. error code: ${err.code}`);
  }
}
```

## setExposureBias<sup>11+</sup>

setExposureBias(exposureBias: number): void

Sets the exposure compensation, which is the exposure value (EV).

Before making the setting, it is recommended to first query the supported range through the method [getExposureBiasRange](arkts-apis-camera-AutoExposureQuery.md#getexposurebiasrange11).

**Atomic service API**: This API can be used in atomic services since API version 19.

**System Capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Parameter Name     | Type                            | Mandatory | Description                                                                                                                                                                                            |
| -------- | -------------------------------| ---- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| exposureBias   | number                   | Yes   | Exposure Compensation. [getExposureBiasRange](arkts-apis-camera-AutoExposureQuery.md#getexposurebiasrange11) queries the supported range. If a value exceeding the supported range is set, it is automatically matched to the nearest critical point.<br>Exposure Compensation has a step size, which varies due to device differences. For example, if the step size is 0.5, setting 1.2 will result in an actual effective Exposure Compensation of 1.0.<br>If the API call fails, the corresponding Error Code will be returned. For details about the Error Code type, see [CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode). |

**Error codes**

For details about the following Error Codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code         | Error Message        |
| --------------- | --------------- |
| 7400102                |  Operation not allowed.                                |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setExposureBias(photoSession: camera.PhotoSession, biasRangeArray: Array<number>): void {
  if (biasRangeArray && biasRangeArray.length > 0) {
    let exposureBias = biasRangeArray[0];
    try {
      photoSession.setExposureBias(exposureBias);
    } catch (error) {
      // If failed, return the error code error.code and handle it.
      let err = error as BusinessError;
      console.error(`The setExposureBias call failed. error code: ${err.code}`);
    }
  }
}
```

## getExposureValue<sup>11+</sup>

getExposureValue(): number

Queries the current exposure value.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Return value**

| Type        | Description                          |
| ---------- | ----------------------------- |
| number    | Gets the exposure value. Exposure compensation has a step size, for example, a step size of 0.5. If 1.2 is set, the actual effective exposure compensation obtained is 1.0.<br>If the API call fails, the corresponding error code will be returned. For details about the error code type, see [CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode). |

**Error codes**

For details about the following error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code         | Error Message        |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getExposureValue(photoSession: camera.PhotoSession): number {
  const invalidValue: number = -1;
  let exposureValue: number = invalidValue;
  try {
    exposureValue = photoSession.getExposureValue();
  } catch (error) {
    // If it fails, an error code error.code is returned and needs to be handled.
    let err = error as BusinessError;
    console.error(`The getExposureValue call failed. error code: ${err.code}`);
  }
  return exposureValue;
}
```

## getExposureMeteringMode<sup>24+</sup>

getExposureMeteringMode(): ExposureMeteringMode

Obtains the current exposure metering mode.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System Capability:** SystemCapability.Multimedia.Camera.Core

**Return value**

| Type        | Description                          |
| ---------- | ----------------------------- |
| [ExposureMeteringMode](arkts-apis-camera-e.md#exposuremeteringmode24)    | Current exposure metering mode. |

**Error codes**

For details about the following error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code         | Error Message        |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config, only throw in session usage.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getExposureMeteringMode(photoSession: camera.PhotoSession): camera.ExposureMeteringMode {
  let meteringMode: camera.ExposureMeteringMode = camera.ExposureMeteringMode.MATRIX;
  try {
    meteringMode = photoSession.getExposureMeteringMode();
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The getExposureMeteringMode call failed. error code: ${err.code}`);
  }
  return meteringMode;
}
```

## setExposureMeteringMode<sup>24+</sup>

setExposureMeteringMode(aeMeteringMode: ExposureMeteringMode): void

Sets the exposure metering mode.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System Capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Name      | Type                           | Mandatory  | Description                           |
| -------- | -------------------------------| ---- | ----------------------------- |
| aeMeteringMode   | [ExposureMeteringMode](arkts-apis-camera-e.md#exposuremeteringmode24)  | Yes   | Exposure metering mode.                 |

**Error codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| Error Code         | Error Message        |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config, only throw in session usage.                                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setExposureMeteringMode(photoSession: camera.PhotoSession, aeMeteringMode: camera.ExposureMeteringMode): void {
  try {
    photoSession.setExposureMeteringMode(aeMeteringMode);
  } catch (error) {
    // If the operation fails, an error code is returned in error.code and needs to be handled.
    let err = error as BusinessError;
    console.error(`The setExposureMeteringMode call failed. error code: ${err.code}`);
  }
}
```