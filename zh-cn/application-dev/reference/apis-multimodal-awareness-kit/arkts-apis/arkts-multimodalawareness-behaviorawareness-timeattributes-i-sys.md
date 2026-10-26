# TimeAttributes（系统接口）

```TypeScript
export interface TimeAttributes
```

时间类场景属性。

**起始版本：** 26.1.0

<!--Device-behaviorAwareness-export interface TimeAttributes--><!--Device-behaviorAwareness-export interface TimeAttributes-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## dayOfMonth

```TypeScript
dayOfMonth?: number
```

每月的第几天。单位：天。取值需为 [1,31] 范围内的整数。默认值：默认值为 0。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeAttributes-dayOfMonth?: int--><!--Device-TimeAttributes-dayOfMonth?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## dayOfWeek

```TypeScript
dayOfWeek?: number
```

星期几。取值需为 [1,7] 范围内的整数。默认值：默认值为 0。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeAttributes-dayOfWeek?: int--><!--Device-TimeAttributes-dayOfWeek?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## kind

```TypeScript
kind: 'time'
```

判别字段，固定为 'time'。

**类型：** 'time'

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeAttributes-kind: 'time'--><!--Device-TimeAttributes-kind: 'time'-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## recurrence

```TypeScript
recurrence: RecurrenceType
```

重复周期。

**类型：** [RecurrenceType](arkts-multimodalawareness-behaviorawareness-recurrencetype-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeAttributes-recurrence: RecurrenceType--><!--Device-TimeAttributes-recurrence: RecurrenceType-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## timePoint

```TypeScript
timePoint: string
```

时间点（HH:mm 格式，如 "08:30"）。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeAttributes-timePoint: string--><!--Device-TimeAttributes-timePoint: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。
