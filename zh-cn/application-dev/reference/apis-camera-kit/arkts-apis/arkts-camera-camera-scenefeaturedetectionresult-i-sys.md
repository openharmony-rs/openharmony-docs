# SceneFeatureDetectionResult（系统接口）

```TypeScript
interface SceneFeatureDetectionResult
```

场景特性检测结果。

**起始版本：** 12

<!--Device-camera-interface SceneFeatureDetectionResult--><!--Device-camera-interface SceneFeatureDetectionResult-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## detected

```TypeScript
readonly detected: boolean
```

是否检测到指定的场景特性。**true**表示检测到，**false**表示未检测到。

**类型：** boolean

**起始版本：** 12

<!--Device-SceneFeatureDetectionResult-readonly detected: boolean--><!--Device-SceneFeatureDetectionResult-readonly detected: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## featureType

```TypeScript
readonly featureType: SceneFeatureType
```

场景特性类型。

**类型：** [SceneFeatureType](arkts-camera-camera-scenefeaturetype-e-sys.md)

**起始版本：** 12

<!--Device-SceneFeatureDetectionResult-readonly featureType: SceneFeatureType--><!--Device-SceneFeatureDetectionResult-readonly featureType: SceneFeatureType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
