# @ohos.multimodalAwareness.spatialAwareness(空间感知)

本模块提供对测距的感知能力，支持超声信号测试。@namespace spatialAwareness

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [offDistanceMeasure](arkts-multimodalawareness-spatialawareness-offdistancemeasure-f-sys.md) | 取消订阅测距接口。停止运行已订阅的测距算法。 |
| [offIndoorOrOutdoorIdentify](arkts-multimodalawareness-spatialawareness-offindoororoutdooridentify-f-sys.md) | 取消订阅门内外识别接口。停止运行已订阅的门内外识别算法。 |
| [onDistanceMeasure](arkts-multimodalawareness-spatialawareness-ondistancemeasure-f-sys.md) | 订阅测距接口。触发测距算法执行，并返回测距结果。 |
| [onIndoorOrOutdoorIdentify](arkts-multimodalawareness-spatialawareness-onindoororoutdooridentify-f-sys.md) | 订阅门内外识别接口。触发门内外识别算法执行，并返回设备在门内还是门外的信息。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DistanceMeasurementConfigParams](arkts-multimodalawareness-spatialawareness-distancemeasurementconfigparams-i-sys.md) | 测距接口的输入参数配置。根据不同的参数配置，执行对应的算法。@interface DistanceMeasurementConfigParams |
| [DistanceMeasurementResponse](arkts-multimodalawareness-spatialawareness-distancemeasurementresponse-i-sys.md) | 测距接口执行完成后的回调结果。@interface DistanceMeasurementResponse |
| [DoorPositionResponse](arkts-multimodalawareness-spatialawareness-doorpositionresponse-i-sys.md) | 门内外识别接口执行完成后的回调结果。@interface DoorPositionResponse |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DistanceRank](arkts-multimodalawareness-spatialawareness-distancerank-e-sys.md) | 测距结果的距离挡位，不同的挡位对应不同的距离范围。 |
| [PositionRelativeToDoor](arkts-multimodalawareness-spatialawareness-positionrelativetodoor-e-sys.md) | 门内外识别接口返回结果中表示门内或门外位置的枚举。 |
| [ReportingMode](arkts-multimodalawareness-spatialawareness-reportingmode-e-sys.md) | 测距接口执行完成后结果的上报模式。 |
| [TechnologyType](arkts-multimodalawareness-spatialawareness-technologytype-e-sys.md) | 提供输入信号的类型。接口根据输入信号类型，执行对应算法。 |
<!--DelEnd-->
