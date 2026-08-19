# SurfaceParam（系统接口）

Surface configuration parameters.

**起始版本：** 23

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

视频是否翻转。

**类型：** [FlipOptions](arkts-distributedservice-abilityconnectionmanager-flipoptions-e-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceParam-flip?: FlipOptions--><!--Device-SurfaceParam-flip?: FlipOptions-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## format

```TypeScript
format?: VideoPixelFormat
```

视频像素格式，此选项必须在发送端配置。 必须在流启动前设置，设置后不可更新。

**类型：** [VideoPixelFormat](arkts-distributedservice-abilityconnectionmanager-videopixelformat-e-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceParam-format?: VideoPixelFormat--><!--Device-SurfaceParam-format?: VideoPixelFormat-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## height

```TypeScript
height: int
```

编码长度。必须在流启动前设置，设置后不可更新。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceParam-height: int--><!--Device-SurfaceParam-height: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: int
```

视频旋转角度。 旋转角度范围为{0, 90, 180, 270}，默认为0。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceParam-rotation?: int--><!--Device-SurfaceParam-rotation?: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## width

```TypeScript
width: int
```

编码宽度。必须在流启动前设置，设置后不可更新。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceParam-width: int--><!--Device-SurfaceParam-width: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

