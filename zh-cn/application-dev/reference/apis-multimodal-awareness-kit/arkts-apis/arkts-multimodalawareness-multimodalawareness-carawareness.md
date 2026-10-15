# @ohos.multimodalAwareness.carAwareness(车辆感知)

本模块提供车辆感知能力，包括隔空手势交互、实时天气识别、补能状态识别等功能。

**起始版本：** 26.0.1

<!--Device-unnamed-declare namespace carAwareness--><!--Device-unnamed-declare namespace carAwareness-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAllCapabilityList](arkts-multimodalawareness-carawareness-getallcapabilitylist-f.md#getallcapabilitylist) | 获取当前设备支持的所有车辆感知能力列表。 |
| [offRealTimeWeather](arkts-multimodalawareness-carawareness-offrealtimeweather-f.md#offrealtimeweather) | 取消订阅实时天气结果。 |
| [offRefueling](arkts-multimodalawareness-carawareness-offrefueling-f.md#offrefueling) | 取消订阅加油状态结果。 |
| [offSpatialMotion](arkts-multimodalawareness-carawareness-offspatialmotion-f.md#offspatialmotion) | 取消订阅隔空手势结果。 |
| [onRealTimeWeather](arkts-multimodalawareness-carawareness-onrealtimeweather-f.md#onrealtimeweather) | 订阅实时天气感知结果。设备不支持该能力时抛出34000002错误码，可调用getAllCapabilityList查询设备可用能力。通过callback异步返回数据。 |
| [onRefueling](arkts-multimodalawareness-carawareness-onrefueling-f.md#onrefueling) | 订阅补能状态感知结果。设备不支持该能力时抛出34000002错误码，可调用 getAllCapabilityList查询设备可用能力。通过callback异步返回数据。 |
| [onSpatialMotion](arkts-multimodalawareness-carawareness-onspatialmotion-f.md#onspatialmotion) | 订阅隔空手势感知结果。设备不支持该能力时抛出34000002错误码，可调用 getAllCapabilityList查询设备可用能力。通过callback异步返回数据。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getCarAwareness](arkts-multimodalawareness-carawareness-getcarawareness-f-sys.md#getcarawareness) | 单次获取指定类型的车辆感知结果。 |
| [offCarAwareness](arkts-multimodalawareness-carawareness-offcarawareness-f-sys.md#offcarawareness) | 取消订阅指定类型的车辆感知结果。 |
| [onCarAwareness](arkts-multimodalawareness-carawareness-oncarawareness-f-sys.md#oncarawareness) | 订阅车辆感知结果。设备不支持该能力时抛出34000002错误码，可调用getAllCapabilityList查询设备可用能力。通过callback异步返回数据。 |
| [updateSpatialActionEnableStatus](arkts-multimodalawareness-carawareness-updatespatialactionenablestatus-f-sys.md#updatespatialactionenablestatus) | 更新空间动作感知的启停状态。 |
| [updateSpatialActionZone](arkts-multimodalawareness-carawareness-updatespatialactionzone-f-sys.md#updatespatialactionzone) | 更新空间动作感知的音区信息。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [RealTimeWeatherInfo](arkts-multimodalawareness-carawareness-realtimeweatherinfo-i.md) | 实时天气感知的结果信息接口。 |
| [RefuelingInfo](arkts-multimodalawareness-carawareness-refuelinginfo-i.md) | 补能识别的结果信息接口。 |
| [SpatialMotionInfo](arkts-multimodalawareness-carawareness-spatialmotioninfo-i.md) | 隔空手势感知的结果信息接口。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CarAwarenessInfo](arkts-multimodalawareness-carawareness-carawarenessinfo-i-sys.md) | 车辆感知通用结果信息接口。 |
| [CarAwarenessOptions](arkts-multimodalawareness-carawareness-carawarenessoptions-i-sys.md) | 车辆感知订阅配置选项接口。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Capability](arkts-multimodalawareness-carawareness-capability-e.md) | 表示车辆感知支持的能力类型枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Capability](arkts-multimodalawareness-carawareness-capability-e-sys.md) | 表示车辆感知支持的能力类型枚举。 |
<!--DelEnd-->
