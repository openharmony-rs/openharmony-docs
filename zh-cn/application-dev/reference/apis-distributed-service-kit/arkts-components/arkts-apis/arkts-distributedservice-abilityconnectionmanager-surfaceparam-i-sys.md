# SurfaceParam（系统接口）

Surface配置参数。

@interface SurfaceParam

**起始版本：** 18

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

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## format

```TypeScript
format?: VideoPixelFormat
```

视频像素格式，此选项必须在发送端配置。必须在流启动前设置，设置后不可更新。

**类型：** [VideoPixelFormat](arkts-distributedservice-abilityconnectionmanager-videopixelformat-e-sys.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## height

```TypeScript
height: number
```

表示编码高度。必须在流启动前设置，流启动后到停止前均无法更新。如需更新需要将流停止后重新配置。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: number
```

表示视频的旋转角度（取值范围为{0, 90, 180, 270}，默认值为0）。0表示不旋转，90表示向右旋转90度（适合竖屏视频），180表示旋转180度，270表示向左旋转90度。不传入时默认为0。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## width

```TypeScript
width: number
```

表示编码宽度。必须在流启动前设置，流启动后到停止前均无法更新。如需更新需要将流停止后重新配置。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。
