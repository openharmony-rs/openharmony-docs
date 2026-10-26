# PerceptionEvent（系统接口）

```TypeScript
export interface PerceptionEvent<T = BehaviorAwarenessPayload>
```

感知事件数据。MSDP 融合感知聚类后生成的事件，推送给业务侧。

**起始版本：** 26.1.0

<!--Device-behaviorAwareness-export interface PerceptionEvent<T = BehaviorAwarenessPayload>--><!--Device-behaviorAwareness-export interface PerceptionEvent<T = BehaviorAwarenessPayload>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## confidence

```TypeScript
confidence: number
```

置信度。值 0 表示无置信度，值 100 表示完全确定。单位：百分比。取值需为 [0,100] 范围内的整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PerceptionEvent-confidence: int--><!--Device-PerceptionEvent-confidence: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## domain

```TypeScript
domain: PerceptionDomain
```

感知领域类型。

**类型：** [PerceptionDomain](arkts-multimodalawareness-behaviorawareness-perceptiondomain-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PerceptionEvent-domain: PerceptionDomain--><!--Device-PerceptionEvent-domain: PerceptionDomain-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## generateTime

```TypeScript
generateTime: number
```

生成时间戳。单位：毫秒。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PerceptionEvent-generateTime: long--><!--Device-PerceptionEvent-generateTime: long-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## payload

```TypeScript
payload: T
```

领域特定数据。

**类型：** T

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PerceptionEvent-payload: T--><!--Device-PerceptionEvent-payload: T-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## perceptionEventId

```TypeScript
perceptionEventId: string
```

感知事件唯一标识。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PerceptionEvent-perceptionEventId: string--><!--Device-PerceptionEvent-perceptionEventId: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。
