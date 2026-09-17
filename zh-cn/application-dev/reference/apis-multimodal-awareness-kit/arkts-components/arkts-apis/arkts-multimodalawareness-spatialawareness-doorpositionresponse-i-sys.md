# DoorPositionResponse（系统接口）

门内外识别接口执行完成后的回调结果。@interface DoorPositionResponse

**起始版本：** 23

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## deviceId

```TypeScript
deviceId: string
```

表示设备Id号，字符串长度：[1,128]。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## doorLockCode

```TypeScript
doorLockCode: number
```

表示门锁校验码，结果≥0。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## position

```TypeScript
position: PositionRelativeToDoor
```

表示门内外位置信息。

**类型：** [PositionRelativeToDoor](arkts-multimodalawareness-spatialawareness-positionrelativetodoor-e-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。
