# PickerProfile

Defines the configuration information about the camera picker.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { cameraPicker } from '@kit.CameraKit';
```

## cameraPosition

```TypeScript
cameraPosition: camera.CameraPosition
```

Camera position.

**Type:** [camera.CameraPosition](arkts-camera-camera-cameraposition-e.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Camera.Core

## saveUri

```TypeScript
saveUri?: string
```

URI for saving the configuration information. For details about the default value, see [File URI](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor). The **saveUri** parameter is optional. If it is not specified, images and videos are automatically saved to the media library. To prevent them from being saved to the media library, specify a valid file path within your application's sandbox. When you use your own resource path, ensure that the file exists and is writable; otherwise, the save operation fails.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Camera.Core

## videoDuration

```TypeScript
videoDuration?: number
```

Maximum video duration, in seconds. The default value is **0**, indicating that the maximum video duration is not set.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Camera.Core
