# RefuelingInfo

```TypeScript
export interface RefuelingInfo
```

补能识别的结果信息接口。

**起始版本：** 26.0.1

<!--Device-carAwareness-export interface RefuelingInfo--><!--Device-carAwareness-export interface RefuelingInfo-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## status

```TypeScript
status: number
```

加油状态。-1：无效0：空闲（未开始加油）1：开始加油2：加油结束。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-RefuelingInfo-status: number--><!--Device-RefuelingInfo-status: number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

## timestamp

```TypeScript
timestamp: number
```

识别结果的时间戳。单位为：ms。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-RefuelingInfo-timestamp: number--><!--Device-RefuelingInfo-timestamp: number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness
