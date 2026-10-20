# TryAEInfo（系统接口）

```TypeScript
interface TryAEInfo
```

描述 Try AE 参数。Try AE 表示硬件在延时拍摄过程中根据环境光照变化上报状态。

**起始版本：** 12

<!--Device-camera-interface TryAEInfo--><!--Device-camera-interface TryAEInfo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## captureInterval

```TypeScript
readonly captureInterval?: number
```

延时拍摄间隔。

**类型：** number

**起始版本：** 12

<!--Device-TryAEInfo-readonly captureInterval?: int--><!--Device-TryAEInfo-readonly captureInterval?: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## isTryAEDone

```TypeScript
readonly isTryAEDone: boolean
```

判断 Try AE 是否已完成。

**类型：** boolean

**起始版本：** 12

<!--Device-TryAEInfo-readonly isTryAEDone: boolean--><!--Device-TryAEInfo-readonly isTryAEDone: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## isTryAEHintNeeded

```TypeScript
readonly isTryAEHintNeeded?: boolean
```

判断是否需要 AE 提示。

**类型：** boolean

**起始版本：** 12

<!--Device-TryAEInfo-readonly isTryAEHintNeeded?: boolean--><!--Device-TryAEInfo-readonly isTryAEHintNeeded?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## previewType

```TypeScript
readonly previewType?: TimeLapsePreviewType
```

延时摄影预览类型。

**类型：** [TimeLapsePreviewType](arkts-camera-camera-timelapsepreviewtype-e-sys.md)

**起始版本：** 12

<!--Device-TryAEInfo-readonly previewType?: TimeLapsePreviewType--><!--Device-TryAEInfo-readonly previewType?: TimeLapsePreviewType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
