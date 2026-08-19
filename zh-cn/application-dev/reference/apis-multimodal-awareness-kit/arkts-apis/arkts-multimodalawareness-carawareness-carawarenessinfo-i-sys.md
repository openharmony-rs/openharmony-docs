# CarAwarenessInfo（系统接口）

汽车感知响应信息接口。

**起始版本：** 26.1.0

<!--Device-carAwareness-export interface CarAwarenessInfo--><!--Device-carAwareness-export interface CarAwarenessInfo-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## awarenessEvent

```TypeScript
awarenessEvent?:Record<string, Object>
```

汽车感知数据项列表信息接口。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CarAwarenessInfo-awarenessEvent?:Record<string, Object>--><!--Device-CarAwarenessInfo-awarenessEvent?:Record<string, Object>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**系统接口：** 此接口为系统接口。

## capability

```TypeScript
capability: Capability
```

表示特定能力。

**类型：** Capability

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CarAwarenessInfo-capability: Capability--><!--Device-CarAwarenessInfo-capability: Capability-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp: number
```

时间戳。 单位为：毫秒。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CarAwarenessInfo-timestamp: number--><!--Device-CarAwarenessInfo-timestamp: number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**系统接口：** 此接口为系统接口。

