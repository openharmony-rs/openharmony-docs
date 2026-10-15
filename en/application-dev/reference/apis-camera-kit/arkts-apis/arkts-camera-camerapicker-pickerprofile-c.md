# PickerProfile

```TypeScript
class PickerProfile
```

Defines the configuration information about the camera picker.

**Since:** 11

<!--Device-cameraPicker-class PickerProfile--><!--Device-cameraPicker-class PickerProfile-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { cameraPicker } from '@kit.CameraKit';
```

## c2PASignatureConfig

```TypeScript
c2PASignatureConfig?: C2PASignatureConfig
```

C2PA signature configuration.

**Type:** [C2PASignatureConfig](arkts-camera-camerapicker-c2pasignatureconfig-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-PickerProfile-c2PASignatureConfig?: C2PASignatureConfig--><!--Device-PickerProfile-c2PASignatureConfig?: C2PASignatureConfig-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## cameraPosition

```TypeScript
cameraPosition: camera.CameraPosition
```

Camera position.

**Type:** [camera.CameraPosition](arkts-camera-camera-cameraposition-e.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerProfile-cameraPosition: camera.CameraPosition--><!--Device-PickerProfile-cameraPosition: camera.CameraPosition-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## enableC2PA

```TypeScript
enableC2PA?: boolean
```

Enables or disables the C2PA signature feature for the photo output.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-PickerProfile-enableC2PA?: boolean--><!--Device-PickerProfile-enableC2PA?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## saveUri

```TypeScript
saveUri?: string
```

URI for saving the configuration information. For details about the default value, see [File URI](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor). The **saveUri** parameter is optional. If it is not specified, images and videos are automatically saved to the media library. To prevent them from being saved to the media library, specify a valid file path within your application's sandbox. When you use your own resource path, ensure that the file exists and is writable; otherwise, the save operation fails.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerProfile-saveUri?: string--><!--Device-PickerProfile-saveUri?: string-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## videoDuration

```TypeScript
videoDuration?: number
```

Maximum video duration, in seconds. The default value is **0**, indicating that the maximum video duration is not set.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerProfile-videoDuration?: int--><!--Device-PickerProfile-videoDuration?: int-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
