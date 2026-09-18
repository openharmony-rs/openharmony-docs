# DistanceMeasurementResponse（系统接口）

测距接口执行完成后的回调结果。@interface DistanceMeasurementResponse

**起始版本：** 23

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## confidence

```TypeScript
confidence: float
```

表示置信度，取值范围：[0,1]。

**类型：** float

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

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

## distance

```TypeScript
distance: float
```

表示距离，结果≥0。

**类型：** float

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## rank

```TypeScript
rank: DistanceRank
```

表示距离档位。

**类型：** [DistanceRank](arkts-multimodalawareness-spatialawareness-distancerank-e-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。
