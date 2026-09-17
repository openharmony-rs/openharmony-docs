# StreamParam（系统接口）

流传输配置的参数。用于配置传输流的传输方式和参数。其中role参数区分发送流（SOURCE）和接收流（SINK），发送流需要配置bitrate和colorSpaceConversionTarget等参数。

@interface StreamParam

**起始版本：** 18

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## bitrate

```TypeScript
bitrate?: number
```

视频码率，默认80(kbps)。仅在发送端有效。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## colorSpaceConversionTarget

```TypeScript
colorSpaceConversionTarget?: colorSpaceManager.ColorSpace
```

表示转换的目标色彩空间。设置该参数后，视频流的色彩空间将转换为目标色彩空间，用于适配不同设备的色彩显示需求。不传此参数时不进行色彩空间转换。

**类型：** [colorSpaceManager.ColorSpace](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

流名称，接收端必须与发送端保持一致。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## role

```TypeScript
role: StreamRole
```

流传输角色，可以是接收流或发送流。

**类型：** [StreamRole](arkts-distributedservice-abilityconnectionmanager-streamrole-e-sys.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。
