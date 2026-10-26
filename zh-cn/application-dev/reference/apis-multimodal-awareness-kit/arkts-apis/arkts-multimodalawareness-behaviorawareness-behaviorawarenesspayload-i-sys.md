# BehaviorAwarenessPayload（系统接口）

```TypeScript
export interface BehaviorAwarenessPayload
```

习惯感知领域 payload。HABIT_AWARENESS 领域的具体数据。

**起始版本：** 26.1.0

<!--Device-behaviorAwareness-export interface BehaviorAwarenessPayload--><!--Device-behaviorAwareness-export interface BehaviorAwarenessPayload-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## action

```TypeScript
action: ActionData[]
```

关联动作。

**类型：** [ActionData](arkts-multimodalawareness-behaviorawareness-actiondata-i-sys.md)[]

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BehaviorAwarenessPayload-action: ActionData[]--><!--Device-BehaviorAwarenessPayload-action: ActionData[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## patternType

```TypeScript
patternType: PatternType
```

感知模式类型。

**类型：** [PatternType](arkts-multimodalawareness-behaviorawareness-patterntype-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BehaviorAwarenessPayload-patternType: PatternType--><!--Device-BehaviorAwarenessPayload-patternType: PatternType-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## triggerEvent

```TypeScript
triggerEvent: EventData[]
```

触发事件。

**类型：** [EventData](arkts-multimodalawareness-behaviorawareness-eventdata-i-sys.md)[]

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BehaviorAwarenessPayload-triggerEvent: EventData[]--><!--Device-BehaviorAwarenessPayload-triggerEvent: EventData[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。
