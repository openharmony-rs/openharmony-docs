# RealTimeWeatherInfo

```TypeScript
export interface RealTimeWeatherInfo
```

实时天气感知的结果信息接口。

**起始版本：** 26.0.1

<!--Device-carAwareness-export interface RealTimeWeatherInfo--><!--Device-carAwareness-export interface RealTimeWeatherInfo-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## timestamp

```TypeScript
timestamp: number
```

识别结果的时间戳。单位为：ms。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RealTimeWeatherInfo-timestamp: number--><!--Device-RealTimeWeatherInfo-timestamp: number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

## weather

```TypeScript
weather: number
```

天气状态。-1：无效0：其他1：雾2：浓雾3：雪4：大雪5：雨6：大雨。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RealTimeWeatherInfo-weather: number--><!--Device-RealTimeWeatherInfo-weather: number-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness
