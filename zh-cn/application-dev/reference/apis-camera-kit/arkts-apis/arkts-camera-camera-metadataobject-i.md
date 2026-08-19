# MetadataObject

相机元能力信息，[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput.on('metadataObjectsAvailable')接口获取。

**起始版本：** 23

<!--Device-camera-interface MetadataObject--><!--Device-camera-interface MetadataObject-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## boundingBox

```TypeScript
readonly boundingBox: Rect
```

metadata 区域框。

**类型：** Rect

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataObject-readonly boundingBox: Rect--><!--Device-MetadataObject-readonly boundingBox: Rect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isLockFocusTracked

```TypeScript
readonly isLockFocusTracked?: boolean
```

是否已锁定焦点跟踪。true表示已锁定，false表示未锁定。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataObject-readonly isLockFocusTracked?: boolean--><!--Device-MetadataObject-readonly isLockFocusTracked?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## timestamp

```TypeScript
readonly timestamp: int
```

当前时间戳。单位为纳秒（ns）。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataObject-readonly timestamp: int--><!--Device-MetadataObject-readonly timestamp: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## type

```TypeScript
readonly type: MetadataObjectType
```

metadata 类型。

**类型：** [MetadataObjectType](arkts-camera-camera-metadataobjecttype-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataObject-readonly type: MetadataObjectType--><!--Device-MetadataObject-readonly type: MetadataObjectType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

