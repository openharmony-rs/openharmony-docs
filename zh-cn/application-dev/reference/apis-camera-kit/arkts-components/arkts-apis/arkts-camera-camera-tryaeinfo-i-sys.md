# TryAEInfo（系统接口）

Describes the Try AE parameters. Try AE indicates that the hardware reports the status based on the ambient illumination change during time-lapse photographing.

**起始版本：** 12

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

Timelapse capture interval.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## isTryAEDone

```TypeScript
readonly isTryAEDone: boolean
```

Determine whether try AE is done.

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## isTryAEHintNeeded

```TypeScript
readonly isTryAEHintNeeded?: boolean
```

Determine whether AE hint is needed.

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## previewType

```TypeScript
readonly previewType?: TimeLapsePreviewType
```

Timelapse preview type.

**类型：** [TimeLapsePreviewType](arkts-camera-camera-timelapsepreviewtype-e-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
