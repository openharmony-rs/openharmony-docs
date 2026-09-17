# @ohos.multimedia.cameraPicker(Camera Picker)

The module provides APIs for an application to use the system camera to take photos or record videos, depending on the media type specified by the application. The application must call these APIs within a UIAbility. Otherwise, the camera picker cannot be started.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { cameraPicker } from '@kit.CameraKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [pick](arkts-camera-camerapicker-pick-f.md) | Starts the camera picker and enters the corresponding mode based on the media type. This API uses a promise to return the result. |

### Classes

| Name | Description |
| --- | --- |
| [PickerProfile](arkts-camera-camerapicker-pickerprofile-c.md) | Defines the configuration information about the camera picker. |
| [PickerResult](arkts-camera-camerapicker-pickerresult-c.md) | Defines the processing result of the camera picker. |

### Enums

| Name | Description |
| --- | --- |
| [PickerMediaType](arkts-camera-camerapicker-pickermediatype-e.md) | Enumerates the media types displayed in the camera picker. |
