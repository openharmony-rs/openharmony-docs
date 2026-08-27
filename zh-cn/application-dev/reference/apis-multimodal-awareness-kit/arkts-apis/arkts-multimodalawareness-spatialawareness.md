# @ohos.multimodalAwareness.spatialAwareness(空间感知)

本模块提供对测距的感知能力，支持超声信号测试。 @namespace spatialAwareness

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
| [offDistanceMeasure(空间感知)](arkts-multimodalawareness-spatialawareness-offdistancemeasure-f-sys.md) | 取消订阅测距接口。停止运行已订阅的测距算法。 |
| [offIndoorOrOutdoorIdentify(空间感知)](arkts-multimodalawareness-spatialawareness-offindoororoutdooridentify-f-sys.md) | 取消订阅门内外识别接口。停止运行已订阅的门内外识别算法。 |
| [onDistanceMeasure(空间感知)](arkts-multimodalawareness-spatialawareness-ondistancemeasure-f-sys.md) | 订阅测距接口。触发测距算法执行，并返回测距结果。 |
| [onIndoorOrOutdoorIdentify(空间感知)](arkts-multimodalawareness-spatialawareness-onindoororoutdooridentify-f-sys.md) | 订阅门内外识别接口。触发门内外识别算法执行，并返回设备在门内还是门外的信息。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DistanceMeasurementConfigParams(空间感知)](arkts-multimodalawareness-spatialawareness-distancemeasurementconfigparams-i-sys.md) | 测距接口的输入参数配置。根据不同的参数配置，执行对应的算法。 @interface DistanceMeasurementConfigParams |
| [DistanceMeasurementResponse(空间感知)](arkts-multimodalawareness-spatialawareness-distancemeasurementresponse-i-sys.md) | 测距接口执行完成后的回调结果。 @interface DistanceMeasurementResponse |
| [DoorPositionResponse(空间感知)](arkts-multimodalawareness-spatialawareness-doorpositionresponse-i-sys.md) | 门内外识别接口执行完成后的回调结果。 @interface DoorPositionResponse |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DistanceRank(空间感知)](arkts-multimodalawareness-spatialawareness-distancerank-e-sys.md) | 测距结果的距离挡位，不同的挡位对应不同的距离范围。@enum { string } 表示测距距离类型 |
| [PositionRelativeToDoor(空间感知)](arkts-multimodalawareness-spatialawareness-positionrelativetodoor-e-sys.md) | 门内外识别接口返回结果中表示门内或门外位置的枚举。@enum { number } 门内外识别结果的枚举 |
| [ReportingMode(空间感知)](arkts-multimodalawareness-spatialawareness-reportingmode-e-sys.md) | 测距接口执行完成后结果的上报模式。@enum { number } 测距结果上报方式 |
| [TechnologyType(空间感知)](arkts-multimodalawareness-spatialawareness-technologytype-e-sys.md) | 提供输入信号的类型。接口根据输入信号类型，执行对应算法。@enum { number } 测距技术类型 |
<!--DelEnd-->
