# Coordinates（系统接口）

```TypeScript
export interface Coordinates
```

地理坐标。

**起始版本：** 26.1.0

<!--Device-behaviorAwareness-export interface Coordinates--><!--Device-behaviorAwareness-export interface Coordinates-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## latitude

```TypeScript
latitude: number
```

纬度。单位：度。取值范围：[-90,90]。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Coordinates-latitude: double--><!--Device-Coordinates-latitude: double-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## longitude

```TypeScript
longitude: number
```

经度。单位：度。取值范围：[-180,180]。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Coordinates-longitude: double--><!--Device-Coordinates-longitude: double-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。
