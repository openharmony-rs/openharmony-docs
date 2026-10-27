# SubscribeInfo（系统接口）

```TypeScript
export interface SubscribeInfo
```

订阅选项。定义订阅的过滤条件。

**起始版本：** 26.1.0

<!--Device-behaviorAwareness-export interface SubscribeInfo--><!--Device-behaviorAwareness-export interface SubscribeInfo-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## domain

```TypeScript
domain: PerceptionDomain
```

感知领域类型。

**类型：** [PerceptionDomain](arkts-multimodalawareness-behaviorawareness-perceptiondomain-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubscribeInfo-domain: PerceptionDomain--><!--Device-SubscribeInfo-domain: PerceptionDomain-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## patternTypes

```TypeScript
patternTypes?: PatternType[]
```

子类型过滤（可选。不指定时订阅该领域下所有模式。）。默认值：不过滤，订阅该领域下所有子类型。

**类型：** [PatternType](arkts-multimodalawareness-behaviorawareness-patterntype-e-sys.md)[]

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubscribeInfo-patternTypes?: PatternType[]--><!--Device-SubscribeInfo-patternTypes?: PatternType[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。
