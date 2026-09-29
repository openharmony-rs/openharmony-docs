# @ohos.multimodalAwareness.deviceStatus(Device status awareness)

This module provides the capability of sensing the device status. It senses the physical status of the device in real time through sensors, helping you adjust application behavior based on the physical status of the device.

**Since:** 18

<!--Device-unnamed-declare namespace deviceStatus--><!--Device-unnamed-declare namespace deviceStatus-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

## Modules to Import

```TypeScript
import { deviceStatus } from '@kit.MultimodalAwarenessKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [off](arkts-multimodalawareness-devicestatus-off-f.md#offsteadystandingdetect) | Unsubscribes from steady standing state events. |
| [on](arkts-multimodalawareness-devicestatus-on-f.md#onsteadystandingdetect) | Subscribes to the device steady standing state (stand mode) event. It is recommended to call off() to unsubscribe when it is no longer needed to release resources. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getDeviceRotationRadian](arkts-multimodalawareness-devicestatus-getdevicerotationradian-f-sys.md) | Obtains the device posture data. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DeviceRotationRadian](arkts-multimodalawareness-devicestatus-devicerotationradian-i-sys.md) | Interface for device rotation radian |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [SteadyStandingStatus](arkts-multimodalawareness-devicestatus-steadystandingstatus-e.md) | Defines the steady standing state (that is, stand mode). |
