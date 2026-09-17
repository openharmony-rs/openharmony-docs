# SceneFeatureDetectionResult（系统接口）

Describes the scene feature detection result.

**起始版本：** 12

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

Whether the specified scene feature is detected. **true** if detected, **false** otherwise.

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## featureType

```TypeScript
readonly featureType: SceneFeatureType
```

Scene feature type.

**类型：** [SceneFeatureType](arkts-camera-camera-scenefeaturetype-e-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
