# EventData（系统接口）

```TypeScript
export interface EventData
```

事件数据。

**起始版本：** 26.1.0

<!--Device-behaviorAwareness-export interface EventData--><!--Device-behaviorAwareness-export interface EventData-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## attributes

```TypeScript
attributes?: TimeAttributes | LocationAttributes | SystemEventAttributes
```

场景属性。

**类型：** [TimeAttributes](arkts-multimodalawareness-behaviorawareness-timeattributes-i-sys.md) &#124; [LocationAttributes](arkts-multimodalawareness-behaviorawareness-locationattributes-i-sys.md) &#124; [SystemEventAttributes](arkts-multimodalawareness-behaviorawareness-systemeventattributes-i-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventData-attributes?: TimeAttributes | LocationAttributes | SystemEventAttributes--><!--Device-EventData-attributes?: TimeAttributes | LocationAttributes | SystemEventAttributes-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## eventId

```TypeScript
eventId: string
```

事件 ID。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventData-eventId: string--><!--Device-EventData-eventId: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## eventType

```TypeScript
eventType: EventType
```

事件类型。

**类型：** [EventType](arkts-multimodalawareness-behaviorawareness-eventtype-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventData-eventType: EventType--><!--Device-EventData-eventType: EventType-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

事件名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventData-name: string--><!--Device-EventData-name: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## params

```TypeScript
params?: Record<string, string | number | boolean>
```

附加参数。默认值：无附加参数时的默认行为。

**类型：** Record&lt;string, string &#124; number &#124; boolean&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventData-params?: Record<string, string | int | boolean>--><!--Device-EventData-params?: Record<string, string | int | boolean>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp: number
```

发生时间戳。单位：毫秒。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventData-timestamp: long--><!--Device-EventData-timestamp: long-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。
