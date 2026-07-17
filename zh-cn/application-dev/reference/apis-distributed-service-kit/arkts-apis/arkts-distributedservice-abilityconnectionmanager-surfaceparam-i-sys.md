# SurfaceParam（系统接口）

Surface configuration parameters.

**起始版本：** 18

<!--Device-abilityConnectionManager-interface SurfaceParam--><!--Device-abilityConnectionManager-interface SurfaceParam-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## flip

```TypeScript
flip?: FlipOptions
```

This value indicates whether the video is reversed.

**类型：** FlipOptions

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceParam-flip?: FlipOptions--><!--Device-SurfaceParam-flip?: FlipOptions-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## format

```TypeScript
format?: VideoPixelFormat
```

Video PixelFormat, this option must be configured on the sender.Must be set before stream starts and cannot update once set.

**类型：** VideoPixelFormat

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceParam-format?: VideoPixelFormat--><!--Device-SurfaceParam-format?: VideoPixelFormat-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## height

```TypeScript
height: number
```

Encoding length. Must be set before stream starts and cannot update once set.

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceParam-height: int--><!--Device-SurfaceParam-height: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: number
```

This value identifies the rotation angle of the video.the range of rotation angle should be {0, 90, 180, 270}, default is 0

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceParam-rotation?: int--><!--Device-SurfaceParam-rotation?: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## width

```TypeScript
width: number
```

Encoding width. Must be set before stream starts and cannot update once set.

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceParam-width: int--><!--Device-SurfaceParam-width: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

