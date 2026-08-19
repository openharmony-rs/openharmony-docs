# PhotoSessionForSys（系统接口）

Implements a photo session for system applications, which sets the parameters of the normal photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md).

**继承/实现关系：** PhotoSessionForSys extends [PhotoSession](arkts-camera-camera-photosession-i.md), [Beauty](arkts-camera-camera-beauty-i-sys.md), [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md), [ColorManagement](arkts-camera-camera-colormanagement-i.md), [Macro](arkts-camera-camera-macro-i-sys.md), [SceneDetection](arkts-camera-camera-scenedetection-i-sys.md), [EffectSuggestion](arkts-camera-camera-effectsuggestion-i-sys.md), [DepthFusion](arkts-camera-camera-depthfusion-i-sys.md), [ImagingMode](arkts-camera-camera-imagingmode-i-sys.md)

**起始版本：** 23

<!--Device-camera-interface PhotoSessionForSys--><!--Device-camera-interface PhotoSessionForSys-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

