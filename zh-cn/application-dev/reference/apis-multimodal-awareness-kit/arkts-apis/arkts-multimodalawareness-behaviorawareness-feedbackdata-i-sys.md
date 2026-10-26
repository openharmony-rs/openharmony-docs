# FeedbackData（系统接口）

```TypeScript
export interface FeedbackData
```

反馈数据。

**起始版本：** 26.1.0

<!--Device-behaviorAwareness-export interface FeedbackData--><!--Device-behaviorAwareness-export interface FeedbackData-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## feedbackTime

```TypeScript
feedbackTime: number
```

反馈时间戳。单位：毫秒。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeedbackData-feedbackTime: long--><!--Device-FeedbackData-feedbackTime: long-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## feedbackType

```TypeScript
feedbackType: FeedbackType
```

反馈类型。

**类型：** [FeedbackType](arkts-multimodalawareness-behaviorawareness-feedbacktype-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeedbackData-feedbackType: FeedbackType--><!--Device-FeedbackData-feedbackType: FeedbackType-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## perceptionEventId

```TypeScript
perceptionEventId: string
```

感知事件 ID。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeedbackData-perceptionEventId: string--><!--Device-FeedbackData-perceptionEventId: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。
