# VideoSessionForSys（系统接口）

```TypeScript
interface VideoSessionForSys extends VideoSession, Beauty, ColorEffect, ColorManagement, Macro, Aperture, ColorReservation, EffectSuggestion, ImagingMode
```

为系统应用实现视频会话，用于设置普通视频模式的参数，并保存运行相机所需的所有[CameraInput](arkts-camera-camera-camerainput-i.md)和[CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。此接口继承自[Session](arkts-camera-camera-session-i.md)。

**继承/实现关系：** VideoSessionForSys extends [VideoSession](arkts-camera-camera-videosession-i.md)<!--Del-->, [Beauty](arkts-camera-camera-beauty-i-sys.md)<!--DelEnd--><!--Del-->, [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md)<!--DelEnd-->, [ColorManagement](arkts-camera-camera-colormanagement-i.md), [Macro](arkts-camera-camera-macro-i.md), [Aperture](arkts-camera-camera-aperture-i.md)<!--Del-->, [ColorReservation](arkts-camera-camera-colorreservation-i-sys.md)<!--DelEnd--><!--Del-->, [EffectSuggestion](arkts-camera-camera-effectsuggestion-i-sys.md)<!--DelEnd--><!--Del-->, [ImagingMode](arkts-camera-camera-imagingmode-i-sys.md)<!--DelEnd-->

**起始版本：** 11

<!--Device-camera-interface VideoSessionForSys extends VideoSession, Beauty, ColorEffect, ColorManagement, Macro, Aperture, ColorReservation, EffectSuggestion, ImagingMode--><!--Device-camera-interface VideoSessionForSys extends VideoSession, Beauty, ColorEffect, ColorManagement, Macro, Aperture, ColorReservation, EffectSuggestion, ImagingMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```
