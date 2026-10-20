# TripodDetectionResult（系统接口）

```TypeScript
interface TripodDetectionResult extends SceneFeatureDetectionResult
```

TripodDetectionResult extends [SceneFeatureDetectionResult](arkts-camera-camera-scenefeaturedetectionresult-i-sys.md)描述三脚架检测结果。

**继承/实现关系：** TripodDetectionResult extends [SceneFeatureDetectionResult](arkts-camera-camera-scenefeaturedetectionresult-i-sys.md)

**起始版本：** 13

<!--Device-camera-interface TripodDetectionResult extends SceneFeatureDetectionResult--><!--Device-camera-interface TripodDetectionResult extends SceneFeatureDetectionResult-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## tripodStatus

```TypeScript
readonly tripodStatus: TripodStatus
```

三脚架状态。

**类型：** [TripodStatus](arkts-camera-camera-tripodstatus-e-sys.md)

**起始版本：** 13

<!--Device-TripodDetectionResult-readonly tripodStatus: TripodStatus--><!--Device-TripodDetectionResult-readonly tripodStatus: TripodStatus-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
