# Sensor

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor

<!--Device-unnamed-export default class Sensor--><!--Device-unnamed-export default class Sensor-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## getOnBodyState

```TypeScript
static getOnBodyState(options: GetOnBodyStateOptions): void
```

获取设备佩戴状态。此接口为一次性获取，不同于subscribeOnBodyState的持续订阅模式，仅返回当前时刻的佩戴状态。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor.SensorId#WEAR_DETECTION

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static getOnBodyState(options: GetOnBodyStateOptions): void--><!--Device-Sensor-static getOnBodyState(options: GetOnBodyStateOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 获取传感器所在设备穿戴状态时调用。 |

## subscribeAccelerometer

```TypeScript
static subscribeAccelerometer(options: subscribeAccelerometerOptions): void
```

订阅加速度传感器数据变化。通过回调函数获取设备在x、y、z三轴方向上的加速度数据，数据格式为AccelerometerResponse对象，包含x、y、z三个number类型字段。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ACCELEROMETER]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.on(type:

**需要权限：** ohos.permission.ACCELEROMETER

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeAccelerometer(options: subscribeAccelerometerOptions): void--><!--Device-Sensor-static subscribeAccelerometer(options: subscribeAccelerometerOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于设置加速度传感器订阅的参数，包括回调频率和回调函数。 |

## subscribeBarometer

```TypeScript
static subscribeBarometer(options: SubscribeBarometerOptions): void
```

订阅气压计传感器数据变化。通过回调函数获取气压值数据，数据格式为BarometerResponse对象，包含pressure字段（单位：帕斯卡）。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [BAROMETER]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.on(type:

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeBarometer(options: SubscribeBarometerOptions): void--><!--Device-Sensor-static subscribeBarometer(options: SubscribeBarometerOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当气压计传感器数据发生变化时调用。 |

## subscribeCompass

```TypeScript
static subscribeCompass(options: SubscribeCompassOptions): void
```

订阅罗盘传感器数据变化。通过回调函数获取设备面对的方向度数数据，数据格式为CompassResponse对象，包含direction字段。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ORIENTATION]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor.SensorId#ORIENTATION

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeCompass(options: SubscribeCompassOptions): void--><!--Device-Sensor-static subscribeCompass(options: SubscribeCompassOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于设置罗盘传感器订阅的参数，包括回调函数。 |

## subscribeDeviceOrientation

```TypeScript
static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void
```

订阅设备方向传感器数据变化。通过回调函数获取设备方向数据，数据格式为DeviceOrientationResponse对象，包含alpha、beta、gamma三个旋转角度字段（单位：度）。 针对同一个应用，多次调用时，会覆盖前面的调用效果，即仅最后一次调用生效；针对同一个方法内，不支持多次调用。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ORIENTATION]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.on(type:

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void--><!--Device-Sensor-static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于设置设备方向传感器订阅的参数，包括回调频率和回调函数。 |

## subscribeGyroscope

```TypeScript
static subscribeGyroscope(options: SubscribeGyroscopeOptions): void
```

订阅陀螺仪传感器数据变化。通过回调函数获取设备在x、y、z三轴方向的旋转角速度数据，数据格式为GyroscopeResponse对象，包含x、y、z三个number类型字段（单位：rad/s）。 针对同一个应用，多次点击调用时，会覆盖前面的调用效果，即仅最后一次调用生效；针对同一个方法内，不支持多次调用。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [GYROSCOPE]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.on(type:

**需要权限：** ohos.permission.GYROSCOPE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeGyroscope(options: SubscribeGyroscopeOptions): void--><!--Device-Sensor-static subscribeGyroscope(options: SubscribeGyroscopeOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于设置陀螺仪传感器订阅的参数，包括回调频率和回调函数。 |

## subscribeHeartRate

```TypeScript
static subscribeHeartRate(options: SubscribeHeartRateOptions): void
```

订阅心率传感器数据变化。通过回调函数获取心率值数据，数据格式为HeartRateResponse对象，包含heartRate字段（单位：次/分钟），默认回调频率为5秒/次。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [HEART\_RATE]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.on(type:

**需要权限：** ohos.permission.READ_HEALTH_DATA

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeHeartRate(options: SubscribeHeartRateOptions): void--><!--Device-Sensor-static subscribeHeartRate(options: SubscribeHeartRateOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当心率传感器数据发生变化时调用。 |

## subscribeLight

```TypeScript
static subscribeLight(options: SubscribeLightOptions): void
```

订阅环境光传感器数据变化。通过回调函数获取环境光线强度数据，数据格式为LightResponse对象，包含intensity字段（单位：lux）。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [AMBIENT\_LIGHT]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor.SensorId#AMBIENT_LIGHT

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeLight(options: SubscribeLightOptions): void--><!--Device-Sensor-static subscribeLight(options: SubscribeLightOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当环境光传感器数据发生变化时调用。 |

## subscribeOnBodyState

```TypeScript
static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void
```

订阅设备佩戴状态变化。通过回调函数获取设备是否已佩戴的状态数据，数据格式为OnBodyStateResponse对象，包含value字段（boolean类型）。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [WEAR\_DETECTION]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.on(type:

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void--><!--Device-Sensor-static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当穿着状态改变时调用。 |

## subscribeProximity

```TypeScript
static subscribeProximity(options: SubscribeProximityOptions): void
```

订阅距离传感器数据变化。通过回调函数获取可见物体相对于设备显示屏的接近或远离状态数据，数据格式为ProximityResponse对象，包含distance字段。 > **说明：** > > 从 API version 3开始支持，从API version 8开始废弃。除Lite Wearable外，建议使用 > [PROXIMITY]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor.SensorId#PROXIMITY

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeProximity(options: SubscribeProximityOptions): void--><!--Device-Sensor-static subscribeProximity(options: SubscribeProximityOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于设置距离传感器订阅的参数，包括回调函数。 |

## subscribeStepCounter

```TypeScript
static subscribeStepCounter(options: SubscribeStepCounterOptions): void
```

订阅计步传感器数据变化。通过回调函数获取计步传感器重启后累计记录的步数数据，数据格式为StepCounterResponse对象，包含steps字段。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [PEDOMETER]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.on(type:

**需要权限：** ohos.permission.ACTIVITY_MOTION

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeStepCounter(options: SubscribeStepCounterOptions): void--><!--Device-Sensor-static subscribeStepCounter(options: SubscribeStepCounterOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当步进计数器传感器数据发生变化时调用。 |

## unsubscribeAccelerometer

```TypeScript
static unsubscribeAccelerometer(): void
```

取消订阅加速度传感器数据。调用后，加速度传感器的回调函数将不再触发。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ACCELEROMETER]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.off(type:

**需要权限：** ohos.permission.ACCELEROMETER

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeAccelerometer(): void--><!--Device-Sensor-static unsubscribeAccelerometer(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeBarometer

```TypeScript
static unsubscribeBarometer(): void
```

取消订阅气压计传感器数据。调用后，气压计传感器的回调函数将不再触发。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [BAROMETER]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.off(type:

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeBarometer(): void--><!--Device-Sensor-static unsubscribeBarometer(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeCompass

```TypeScript
static unsubscribeCompass(): void
```

取消订阅罗盘传感器数据。调用后，罗盘传感器的回调函数将不再触发。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ORIENTATION]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.off(type:

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeCompass(): void--><!--Device-Sensor-static unsubscribeCompass(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeDeviceOrientation

```TypeScript
static unsubscribeDeviceOrientation(): void
```

取消订阅设备方向传感器数据。调用后，设备方向传感器的回调函数将不再触发。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ORIENTATION]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.off(type:

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeDeviceOrientation(): void--><!--Device-Sensor-static unsubscribeDeviceOrientation(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeGyroscope

```TypeScript
static unsubscribeGyroscope(): void
```

取消订阅陀螺仪传感器数据。调用后，陀螺仪传感器的回调函数将不再触发。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [GYROSCOPE]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.off(type:

**需要权限：** ohos.permission.GYROSCOPE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeGyroscope(): void--><!--Device-Sensor-static unsubscribeGyroscope(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeHeartRate

```TypeScript
static unsubscribeHeartRate(): void
```

取消订阅心率传感器数据。调用后，心率传感器的回调函数将不再触发。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [HEART\_RATE]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.off(type:

**需要权限：** ohos.permission.READ_HEALTH_DATA

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeHeartRate(): void--><!--Device-Sensor-static unsubscribeHeartRate(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeLight

```TypeScript
static unsubscribeLight(): void
```

取消订阅环境光传感器数据。调用后，环境光传感器的回调函数将不再触发。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [AMBIENT\_LIGHT]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.off(type:

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeLight(): void--><!--Device-Sensor-static unsubscribeLight(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeOnBodyState

```TypeScript
static unsubscribeOnBodyState(): void
```

取消订阅设备佩戴状态。调用后，佩戴状态的回调函数将不再触发。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [WEAR\_DETECTION]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.off(type:

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeOnBodyState(): void--><!--Device-Sensor-static unsubscribeOnBodyState(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeProximity

```TypeScript
static unsubscribeProximity(): void
```

取消订阅距离传感器数据。调用后，距离传感器的回调函数将不再触发。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [PROXIMITY]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.sensor/sensor.SensorId#PROXIMITY

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeProximity(): void--><!--Device-Sensor-static unsubscribeProximity(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeStepCounter

```TypeScript
static unsubscribeStepCounter(): void
```

取消订阅计步传感器数据。调用后，计步传感器的回调函数将不再触发。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [PEDOMETER]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** @ohos.sensor:sensor.off(type:

**需要权限：** ohos.permission.ACTIVITY_MOTION

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeStepCounter(): void--><!--Device-Sensor-static unsubscribeStepCounter(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

