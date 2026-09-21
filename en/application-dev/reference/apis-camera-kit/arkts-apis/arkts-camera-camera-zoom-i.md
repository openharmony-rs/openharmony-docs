# Zoom

```TypeScript
interface Zoom extends ZoomQuery
```

**Zoom** inherits from [ZoomQuery](arkts-camera-camera-zoomquery-i.md).

It provides APIs related to zoom operations.

**Inheritance/Implementation:** Zoom extends [ZoomQuery](arkts-camera-camera-zoomquery-i.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getZoomRatio

```TypeScript
getZoomRatio(): number
```

Obtains the zoom ratio in use.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Zoom ratio obtained. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getZoomRatio(photoSession: camera.PhotoSession): number {
  const invalidValue: number = -1;
  let zoomRatio: number = invalidValue;
  try {
    zoomRatio = photoSession.getZoomRatio();
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The getZoomRatio call failed. error code: ${err.code}`);
  }
  return zoomRatio;
}
```

## setSmoothZoom

```TypeScript
setSmoothZoom(targetRatio: number, mode?: SmoothZoomMode): void
```

Sets smooth zoom.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetRatio | number | Yes | Target zoom ratio. The supported zoom ratio range can be obtained by calling [getZoomRatioRange](arkts-camera-camera-zoomquery-i.md#getzoomratiorange). If the value passed in is not within the supported range, the value within the precision range is retained. |
| mode | [SmoothZoomMode](arkts-camera-camera-smoothzoommode-e.md) | No | Smooth zoom mode. The default value is **0**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config.<br>**Applicable version:** 11 - 17 |

**Examples**

```TypeScript
function setSmoothZoom(sessionExtendsZoom: camera.Zoom, targetZoomRatio: number, mode: camera.SmoothZoomMode): void {
  sessionExtendsZoom.setSmoothZoom(targetZoomRatio, mode);
}
```

## setZoomRatio

```TypeScript
setZoomRatio(zoomRatio: number): void
```

Sets a zoom ratio, with a maximum precision of two decimal places.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| zoomRatio | number | Yes | Zoom ratio. The supported zoom ratio range can be obtained by calling [getZoomRatioRange](arkts-camera-camera-zoomquery-i.md#getzoomratiorange). If the value passed in is not within the supported range, the value within the precision range is retained. <br>It takes some time for the zoom ratio to take effect at the bottom layer. To obtain the correct zoom ratio, you need to wait for one to two frames. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setZoomRatio(photoSession: camera.PhotoSession, zoomRatioRange: Array<number>): void {
  if (zoomRatioRange === undefined || zoomRatioRange.length <= 0) {
    return;
  }
  let zoomRatio = zoomRatioRange[0];
  try {
    photoSession.setZoomRatio(zoomRatio);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The setZoomRatio call failed. error code: ${err.code}`);
  }
}
```
