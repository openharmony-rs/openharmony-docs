# @ohos.multimodalAwareness.carAwareness

此模块提供使用汽车感知的功能

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAllCapabilityList](arkts-multimodalawareness-carawareness-getallcapabilitylist-f.md) | 返回所有能力列表 |
| [offRealTimeWeather](arkts-multimodalawareness-carawareness-offrealtimeweather-f.md) | 关闭实时天气感知功能。 |
| [offRefueling](arkts-multimodalawareness-carawareness-offrefueling-f.md) | 禁用加油感知。 |
| [offSpatialMotion](arkts-multimodalawareness-carawareness-offspatialmotion-f.md) | 关闭空间动作感知，订阅空间动作感知结果。 |
| [onRealTimeWeather](arkts-multimodalawareness-carawareness-onrealtimeweather-f.md) | 开启实时天气感知，订阅实时天气感知结果。如果能力不支持，则不会回调。支持的能力可以通过getAllCapacityList方法获取。 |
| [onRefueling](arkts-multimodalawareness-carawareness-onrefueling-f.md) | 开启加油感知，订阅加油感知结果。如果不支持该功能，将不回调。支持的能力可以通过getAllCapacityList方法获取。 |
| [onSpatialMotion](arkts-multimodalawareness-carawareness-onspatialmotion-f.md) | 开启空间动作感知，订阅空间动作感知结果。如果能力不支持，则不会回调。支持的能力可以通过getAllCapacityList方法获取。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getCarAwareness](arkts-multimodalawareness-carawareness-getcarawareness-f-sys.md) | /**关闭汽车感知，订阅汽车感知结果。 |
| [offCarAwareness](arkts-multimodalawareness-carawareness-offcarawareness-f-sys.md) | 取消订阅汽车感知结果。 |
| [onCarAwareness](arkts-multimodalawareness-carawareness-oncarawareness-f-sys.md) | 开启汽车感知，订阅汽车感知结果。如果不支持该功能，则不会回调，支持的能力可以通过getAllCapacityList方法获取。 |
| [updateSpatialActionEnableStatus](arkts-multimodalawareness-carawareness-updatespatialactionenablestatus-f-sys.md) | 更新感知启用事件，当应用订阅功能时 |
| [updateSpatialActionZone](arkts-multimodalawareness-carawareness-updatespatialactionzone-f-sys.md) | 语音更新声音区域，当语音订阅空间点引擎能力时 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [RealTimeWeatherInfo](arkts-multimodalawareness-carawareness-realtimeweatherinfo-i.md) | 实时天气响应信息接口。 |
| [RefuelingInfo](arkts-multimodalawareness-carawareness-refuelinginfo-i.md) | 加油响应信息接口。 |
| [SpatialMotionInfo](arkts-multimodalawareness-carawareness-spatialmotioninfo-i.md) | 空间运动响应信息的接口。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CarAwarenessInfo](arkts-multimodalawareness-carawareness-carawarenessinfo-i-sys.md) | 汽车感知响应信息接口。 |
| [CarAwarenessOptions](arkts-multimodalawareness-carawareness-carawarenessoptions-i-sys.md) | 汽车感知信息接口 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Capability](arkts-multimodalawareness-carawareness-capability-e.md) | 车辆感知功能。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Capability](arkts-multimodalawareness-carawareness-capability-e-sys.md) | 车辆感知功能。 |
<!--DelEnd-->
