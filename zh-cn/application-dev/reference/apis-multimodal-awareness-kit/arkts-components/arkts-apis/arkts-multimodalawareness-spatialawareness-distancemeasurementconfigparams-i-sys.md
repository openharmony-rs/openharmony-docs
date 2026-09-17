# DistanceMeasurementConfigParams（系统接口）

测距接口的输入参数配置。根据不同的参数配置，执行对应的算法。@interface DistanceMeasurementConfigParams

**起始版本：** 23

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## deviceList

```TypeScript
deviceList: string[]
```

表示设备列表，设备唯一标识符，字符串长度取值范围：[1,128]，数组长度取值范围：[1,128]。

**类型：** string[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## reportFrequency

```TypeScript
reportFrequency: number
```

表示结果上报频率，单位：Hz，取值范围：[0,999999]。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## reportMode

```TypeScript
reportMode: ReportingMode
```

表示结果上报模式。

**类型：** [ReportingMode](arkts-multimodalawareness-spatialawareness-reportingmode-e-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## techType

```TypeScript
techType: TechnologyType
```

表示信号类型。

**类型：** [TechnologyType](arkts-multimodalawareness-spatialawareness-technologytype-e-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。
