# Focus

**Focus** inherits from [FocusQuery](arkts-camera-camera-focusquery-i.md).

It provides APIs related to focus operations.

**Inheritance/Implementation:** Focus extends [FocusQuery](arkts-camera-camera-focusquery-i.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getFocalLength

```TypeScript
getFocalLength(): number
```

Obtains the focal length in use.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Focal length, in mm. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getFocusMode

```TypeScript
getFocusMode(): FocusMode
```

Obtains the focus mode in use.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [FocusMode](arkts-camera-camera-focusmode-e.md) | Focus mode obtained. If the operation fails, undefined is returned and an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getFocusPoint

```TypeScript
getFocusPoint(): Point
```

Obtains the focal point in use.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Point](arkts-camera-camera-point-i.md) | Focal point obtained. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## lockFocusTracking

```TypeScript
lockFocusTracking(focusPoint: Point): void
```

Lock focus tracking.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| focusPoint | [Point](arkts-camera-camera-point-i.md) | Yes | lock focus tracking point. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## setFocusMode

```TypeScript
setFocusMode(afMode: FocusMode): void
```

Sets a focus mode.

Before the setting, call [isFocusModeSupported](arkts-camera-camera-focusquery-i.md#isfocusmodesupported) to check whether the focus mode is supported.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| afMode | [FocusMode](arkts-camera-camera-focusmode-e.md) | Yes | Focus mode. If the input parameter is null or undefined, it is treated as 0 and manual focus is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## setFocusPoint

```TypeScript
setFocusPoint(point: Point): void
```

Sets the focal point. The focal point must be in the coordinate system (0-1), where the top-left corner is {0, 0} and the bottom-right corner is {1, 1}.

The coordinate system is based on the horizontal device direction with the device's charging port on the right. If the layout of the preview screen of an application is based on the vertical direction with the charging port on the lower side, the layout width and height are {w, h}, and the touch point is {x, y}, then the coordinate point after conversion is {y/h, 1-x/w}.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| point | [Point](arkts-camera-camera-point-i.md) | Yes | Focal point. The value range of x and y must be within [0, 1]. If a value less than 0 is passed, the value **0** is used. If a value greater than **1** is passed, the value **1** is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## unlockFocusTracking

```TypeScript
unlockFocusTracking(): void
```

Unlock focus tracking.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |
