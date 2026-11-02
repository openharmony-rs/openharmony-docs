# PhotoSessionForSys（系统接口）

```TypeScript
interface PhotoSessionForSys extends PhotoSession, Beauty, ColorEffect, ColorManagement, Macro, SceneDetection, EffectSuggestion, DepthFusion, ImagingMode
```

系统应用的拍照会话类，用于设置普通拍照模式的参数，并保存运行相机所需的全部[CameraInput](arkts-camera-camera-camerainput-i.md) 和 [CameraOutput](arkts-camera-camera-cameraoutput-i.md) 实例。继承自[Session](arkts-camera-camera-session-i.md)。

**继承/实现关系：** PhotoSessionForSys extends [PhotoSession](arkts-camera-camera-photosession-i.md)<!--Del-->, [Beauty](arkts-camera-camera-beauty-i-sys.md)<!--DelEnd--><!--Del-->, [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md)<!--DelEnd-->, [ColorManagement](arkts-camera-camera-colormanagement-i.md), [Macro](arkts-camera-camera-macro-i.md)<!--Del-->, [SceneDetection](arkts-camera-camera-scenedetection-i-sys.md)<!--DelEnd--><!--Del-->, [EffectSuggestion](arkts-camera-camera-effectsuggestion-i-sys.md)<!--DelEnd--><!--Del-->, [DepthFusion](arkts-camera-camera-depthfusion-i-sys.md)<!--DelEnd--><!--Del-->, [ImagingMode](arkts-camera-camera-imagingmode-i-sys.md)<!--DelEnd-->

**起始版本：** 11

<!--Device-camera-interface PhotoSessionForSys extends PhotoSession, Beauty, ColorEffect, ColorManagement, Macro, SceneDetection, EffectSuggestion, DepthFusion, ImagingMode--><!--Device-camera-interface PhotoSessionForSys extends PhotoSession, Beauty, ColorEffect, ColorManagement, Macro, SceneDetection, EffectSuggestion, DepthFusion, ImagingMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```
