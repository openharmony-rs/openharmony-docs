# SpatialMotionInfo

```TypeScript
export interface SpatialMotionInfo
```

隔空手势感知的结果信息接口。

**起始版本：** 26.0.1

<!--Device-carAwareness-export interface SpatialMotionInfo--><!--Device-carAwareness-export interface SpatialMotionInfo-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## event

```TypeScript
event: number
```

手势事件类型。-1：无效0：准备就绪1：移动2：点击。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SpatialMotionInfo-event: number--><!--Device-SpatialMotionInfo-event: number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

## pointX

```TypeScript
pointX: number
```

手部在屏幕上的 X 轴坐标。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SpatialMotionInfo-pointX: number--><!--Device-SpatialMotionInfo-pointX: number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

## pointY

```TypeScript
pointY: number
```

手部在屏幕上的 Y 轴坐标。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SpatialMotionInfo-pointY: number--><!--Device-SpatialMotionInfo-pointY: number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

## timestamp

```TypeScript
timestamp: number
```

识别结果的时间戳。单位为：ms。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SpatialMotionInfo-timestamp: number--><!--Device-SpatialMotionInfo-timestamp: number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness
