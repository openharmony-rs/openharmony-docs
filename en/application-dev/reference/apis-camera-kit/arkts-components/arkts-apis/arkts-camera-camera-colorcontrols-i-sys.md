# ColorControls (System API)

```TypeScript
interface ColorControls extends ColorControlsQuery
```

Implements color controls. It inherits from [ColorControlsQuery](arkts-camera-camera-colorcontrolsquery-i-sys.md).

**Inheritance/Implementation:** ColorControls extends [ColorControlsQuery](arkts-camera-camera-colorcontrolsquery-i-sys.md)

**Since:** 26.0.1

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getRGBBias

```TypeScript
getRGBBias(): RGBBias
```

Gets RGB bias value.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | The current RGB bias value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getSaturation

```TypeScript
getSaturation(): number
```

Gets the amount of saturation.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | The current saturation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## setRGBBias

```TypeScript
setRGBBias(bias: RGBBias): void
```

Sets RGB bias value.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bias | [RGBBias](arkts-camera-camera-rgbbias-i-sys.md) | Yes | RGB bias value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## setSaturation

```TypeScript
setSaturation(val: number): void
```

Sets the amount of saturation. Before the setting, call [isSaturationSupported](arkts-camera-camera-colorcontrolsquery-i-sys.md#issaturationsupported) to check whether saturation adjustment is supported by the current device.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| val | number | Yes | The amount of saturation to apply. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
