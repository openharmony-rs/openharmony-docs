# PhotoSessionForSys（系统接口）

Implements a photo session for system applications, which sets the parameters of the normal photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md).

@extends PhotoSession, Beauty, ColorEffect, ColorManagement, Macro, SceneDetection, EffectSuggestion [since 11 - 13] @extends PhotoSession, Beauty, ColorEffect, ColorManagement, Macro, SceneDetection, EffectSuggestion, DepthFusion [since 14] @extends PhotoSession, Beauty, ColorEffect, ColorManagement, Macro, SceneDetection, EffectSuggestion, DepthFusion, ImagingMode [since 26.0.0]

**继承/实现关系：** PhotoSessionForSys extends [PhotoSession](arkts-camera-camera-photosession-i.md)<!--Del-->, [Beauty](arkts-camera-camera-beauty-i-sys.md)<!--DelEnd--><!--Del-->, [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md)<!--DelEnd-->, [ColorManagement](arkts-camera-camera-colormanagement-i.md), [Macro](arkts-camera-camera-macro-i.md)<!--Del-->, [SceneDetection](arkts-camera-camera-scenedetection-i-sys.md)<!--DelEnd--><!--Del-->, [EffectSuggestion](arkts-camera-camera-effectsuggestion-i-sys.md)<!--DelEnd--><!--Del-->, [DepthFusion](arkts-camera-camera-depthfusion-i-sys.md)<!--DelEnd--><!--Del-->, [ImagingMode](arkts-camera-camera-imagingmode-i-sys.md)<!--DelEnd-->

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```
