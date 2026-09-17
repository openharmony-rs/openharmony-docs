# ControlCenter

**ControlCenter** inherits from [ControlCenterQuery](arkts-camera-camera-controlcenterquery-i.md).

It is used to enable the camera controller.

**Inheritance/Implementation:** ControlCenter extends [ControlCenterQuery](arkts-camera-camera-controlcenterquery-i.md)

**Since:** 20

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## enableControlCenter

```TypeScript
enableControlCenter(enabled: boolean): void
```

Enables the camera controller.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable or disable the camera controller. **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
