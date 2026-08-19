# Sensor

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [sensor/sensor](arkts-sensor.md)

<!--Device-unnamed-export default class Sensor--><!--Device-unnamed-export default class Sensor-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## 导入模块

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## getOnBodyState

```TypeScript
static getOnBodyState(options: GetOnBodyStateOptions): void
```

获取设备佩戴状态。此接口为一次性获取，不同于subscribeOnBodyState的持续订阅模式，仅返回当前时刻的佩戴状态。 <br>当开发者需要一次性获取设备当前佩戴状态（而非持续监听变化）时，使用此接口。 <br>调用此接口后，系统会通过success回调返回当前佩戴状态数据。此接口不会持续上报数据，仅返回一次结果。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [WEAR_DETECTION](arkts-sensorservice-sensor-sensorid-e.md#wear_detection)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static getOnBodyState(options: GetOnBodyStateOptions): void--><!--Device-Sensor-static getOnBodyState(options: GetOnBodyStateOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetOnBodyStateOptions](arkts-sensorservice-system-sensor-getonbodystateoptions-i.md) | 是 | 获取传感器所在设备佩戴状态时调用。 |

## subscribeAccelerometer

```TypeScript
static subscribeAccelerometer(options: subscribeAccelerometerOptions): void
```

订阅加速度传感器数据变化。通过回调函数获取设备在x、y、z三轴方向上的加速度数据，数据格式为AccelerometerResponse对象，包含x、y、z三个number类型字段。 <br>当开发者需要获取设备加速度信息以实现运动检测、摇一摇等功能时，使用此接口。 <br>调用此接口后，系统会按指定的回调频率上报加速度数据；针对同一个应用，多次调用时，会覆盖前面的调用效果，即仅最后一次调用生效。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ACCELEROMETER](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;, options?: Options)

**需要权限：** ohos.permission.ACCELEROMETER

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeAccelerometer(options: subscribeAccelerometerOptions): void--><!--Device-Sensor-static subscribeAccelerometer(options: subscribeAccelerometerOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [subscribeAccelerometerOptions](arkts-sensorservice-system-sensor-subscribeaccelerometeroptions-i.md) | 是 | 用于设置加速度传感器订阅的参数，包括回调频率和回调函数。 |

## subscribeBarometer

```TypeScript
static subscribeBarometer(options: SubscribeBarometerOptions): void
```

订阅气压计传感器数据变化。通过回调函数获取气压值数据，数据格式为BarometerResponse对象，包含pressure字段，单位：Pa（帕斯卡）。 <br>当开发者需要获取气压信息以实现海拔估算、天气监测、室内导航等功能时，使用此接口。 <br>调用此接口后，系统会在气压数据变化时上报数据；针对同一个应用，多次调用时，会覆盖前面的调用效果，即仅最后一次调用生效。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [BAROMETER](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback&lt;BarometerResponse&gt;, options?: Options)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeBarometer(options: SubscribeBarometerOptions): void--><!--Device-Sensor-static subscribeBarometer(options: SubscribeBarometerOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubscribeBarometerOptions](arkts-sensorservice-system-sensor-subscribebarometeroptions-i.md) | 是 | 当气压计传感器数据发生变化时调用。 |

## subscribeCompass

```TypeScript
static subscribeCompass(options: SubscribeCompassOptions): void
```

订阅罗盘传感器数据变化。通过回调函数获取设备面对的方向度数数据，数据格式为CompassResponse对象，包含direction字段。 <br>当开发者需要获取设备方向信息以实现导航、指南针等功能时，使用此接口。 <br>调用此接口后，系统会在罗盘数据变化时上报方向数据；针对同一个应用，多次调用时，会覆盖前面的调用效果，即仅最后一次调用生效。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ORIENTATION](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [ORIENTATION](arkts-sensorservice-sensor-sensorid-e.md#orientation)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeCompass(options: SubscribeCompassOptions): void--><!--Device-Sensor-static subscribeCompass(options: SubscribeCompassOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubscribeCompassOptions](arkts-sensorservice-system-sensor-subscribecompassoptions-i.md) | 是 | 用于设置罗盘传感器订阅的参数，包括回调函数。 |

## subscribeDeviceOrientation

```TypeScript
static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void
```

订阅设备方向传感器数据变化。通过回调函数获取设备方向数据，数据格式为DeviceOrientationResponse对象，包含alpha、beta、gamma三个旋转角度字段，单位：°（度）。 <br>当开发者需要获取设备方向信息以实现屏幕旋转、游戏方向控制、AR/VR场景等功能时，使用此接口。 <br>针对同一个应用，多次调用时，会覆盖前面的调用效果，即仅最后一次调用生效；针对同一个方法内，不支持多次调用。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ORIENTATION](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor) > 替代。 **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback&lt;OrientationResponse&gt;, options?: Options)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void--><!--Device-Sensor-static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubscribeDeviceOrientationOptions](arkts-sensorservice-system-sensor-subscribedeviceorientationoptions-i.md) | 是 | 用于设置设备方向传感器订阅的参数，包括回调频率和回调函数。 |

## subscribeGyroscope

```TypeScript
static subscribeGyroscope(options: SubscribeGyroscopeOptions): void
```

订阅陀螺仪传感器数据变化。通过回调函数获取设备在x、y、z三轴方向的旋转角速度数据，数据格式为GyroscopeResponse对象，包含x、y、z三个number类型字段，单位：rad/s（弧度/秒）。 <br>当开发者需要获取设备旋转角速度以实现手势识别、游戏操控、姿态追踪等功能时，使用此接口。 <br>针对同一个应用，多次点击调用时，会覆盖前面的调用效果，即仅最后一次调用生效；针对同一个方法内，不支持多次调用。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [GYROSCOPE](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor) > 替代。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;, options?: Options)

**需要权限：** ohos.permission.GYROSCOPE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeGyroscope(options: SubscribeGyroscopeOptions): void--><!--Device-Sensor-static subscribeGyroscope(options: SubscribeGyroscopeOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubscribeGyroscopeOptions](arkts-sensorservice-system-sensor-subscribegyroscopeoptions-i.md) | 是 | 用于设置陀螺仪传感器订阅的参数，包括回调频率和回调函数。 |

## subscribeHeartRate

```TypeScript
static subscribeHeartRate(options: SubscribeHeartRateOptions): void
```

订阅心率传感器数据变化。通过回调函数获取心率值数据，数据格式为HeartRateResponse对象，包含heartRate字段，单位：bpm（beats per minute，每分钟心跳次数），默认回调频率为5秒/次。 <br>当开发者需要获取用户心率数据以实现健康监测、运动强度评估等功能时，使用此接口。 <br>调用此接口后，系统会以5秒/次的频率上报心率数据；针对同一个应用，多次调用时，会覆盖前面的调用效果，即仅最后一次调用生效。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [HEART_RATE](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;, options?: Options)

**需要权限：** ohos.permission.READ_HEALTH_DATA

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeHeartRate(options: SubscribeHeartRateOptions): void--><!--Device-Sensor-static subscribeHeartRate(options: SubscribeHeartRateOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubscribeHeartRateOptions](arkts-sensorservice-system-sensor-subscribeheartrateoptions-i.md) | 是 | 当心率传感器数据发生变化时调用。 |

## subscribeLight

```TypeScript
static subscribeLight(options: SubscribeLightOptions): void
```

订阅环境光传感器数据变化。通过回调函数获取环境光线强度数据，数据格式为LightResponse对象，包含intensity字段，单位：lux（勒克斯）。 <br>当开发者需要获取环境光强度以实现屏幕亮度自动调节、环境光检测等功能时，使用此接口。 <br>再次调用时，会覆盖前一次调用效果，即仅最后一次调用生效。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [AMBIENT_LIGHT](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor) > 替代。 **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [AMBIENT_LIGHT](arkts-sensorservice-sensor-sensorid-e.md#ambient_light)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeLight(options: SubscribeLightOptions): void--><!--Device-Sensor-static subscribeLight(options: SubscribeLightOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubscribeLightOptions](arkts-sensorservice-system-sensor-subscribelightoptions-i.md) | 是 | 当环境光传感器数据发生变化时调用。 |

## subscribeOnBodyState

```TypeScript
static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void
```

订阅设备佩戴状态变化。通过回调函数获取设备是否已佩戴的状态数据，数据格式为OnBodyStateResponse对象，包含value字段（boolean类型）。 <br>当开发者需要检测可穿戴设备是否已被用户佩戴以实现佩戴状态检测、自动启停功能等功能时，使用此接口。 <br>调用此接口后，系统会在佩戴状态变化时上报数据；针对同一个应用，多次调用时，会覆盖前面的调用效果，即仅最后一次调用生效。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [WEAR_DETECTION](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;, options?: Options)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void--><!--Device-Sensor-static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubscribeOnBodyStateOptions](arkts-sensorservice-system-sensor-subscribeonbodystateoptions-i.md) | 是 | 当佩戴状态改变时调用。 |

## subscribeProximity

```TypeScript
static subscribeProximity(options: SubscribeProximityOptions): void
```

订阅距离传感器数据变化。通过回调函数获取可见物体相对于设备显示屏的接近或远离状态数据，数据格式为ProximityResponse对象，包含distance字段。 <br>当开发者需要检测物体与设备屏幕的距离以实现通话时自动息屏、防误触等功能时，使用此接口。 <br>调用此接口后，系统会在距离传感器数据变化时上报数据；针对同一个应用，多次调用时，会覆盖前面的调用效果，即仅最后一次调用生效。 > **说明：** > > 从 API version 3开始支持，从API version 8开始废弃。除Lite Wearable外，建议使用 > [PROXIMITY](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor) > 替代。 **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [PROXIMITY](arkts-sensorservice-sensor-sensorid-e.md#proximity)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeProximity(options: SubscribeProximityOptions): void--><!--Device-Sensor-static subscribeProximity(options: SubscribeProximityOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubscribeProximityOptions](arkts-sensorservice-system-sensor-subscribeproximityoptions-i.md) | 是 | 用于设置距离传感器订阅的参数，包括回调函数。 |

## subscribeStepCounter

```TypeScript
static subscribeStepCounter(options: SubscribeStepCounterOptions): void
```

订阅计步传感器数据变化。通过回调函数获取计步传感器重启后累计记录的步数数据，数据格式为StepCounterResponse对象，包含steps字段。 <br>当开发者需要获取用户步数以实现计步器、运动追踪、健康监测等功能时，使用此接口。 <br>调用此接口后，系统会在计步数据变化时上报数据；针对同一个应用，多次调用时，会覆盖前面的调用效果，即仅最后一次调用生效。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [PEDOMETER](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback&lt;PedometerResponse&gt;, options?: Options)

**需要权限：** ohos.permission.ACTIVITY_MOTION

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static subscribeStepCounter(options: SubscribeStepCounterOptions): void--><!--Device-Sensor-static subscribeStepCounter(options: SubscribeStepCounterOptions): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubscribeStepCounterOptions](arkts-sensorservice-system-sensor-subscribestepcounteroptions-i.md) | 是 | 当步进计数器传感器数据发生变化时调用。 |

## unsubscribeAccelerometer

```TypeScript
static unsubscribeAccelerometer(): void
```

取消订阅加速度传感器数据。调用后，加速度传感器的回调函数将不再触发。 <br>当开发者不再需要加速度数据时（如页面切换、应用退出），使用此接口取消订阅，以减少系统资源占用。 <br>调用此接口后，之前通过subscribeAccelerometer注册的回调函数将不再被触发。如需再次获取数据，需重新调用subscribeAccelerometer。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ACCELEROMETER](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback?: Callback&lt;AccelerometerResponse&gt;)

**需要权限：** ohos.permission.ACCELEROMETER

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeAccelerometer(): void--><!--Device-Sensor-static unsubscribeAccelerometer(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeBarometer

```TypeScript
static unsubscribeBarometer(): void
```

取消订阅气压计传感器数据。调用后，气压计传感器的回调函数将不再触发。 <br>当开发者不再需要气压数据时，使用此接口取消订阅。 <br>调用此接口后，之前通过subscribeBarometer注册的回调函数将不再被触发。需先调用subscribeBarometer订阅后，再调用此接口取消订阅，否则无效果。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [BAROMETER](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback?: Callback&lt;BarometerResponse&gt;)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeBarometer(): void--><!--Device-Sensor-static unsubscribeBarometer(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeCompass

```TypeScript
static unsubscribeCompass(): void
```

取消订阅罗盘传感器数据。调用后，罗盘传感器的回调函数将不再触发。 <br>当开发者不再需要罗盘数据时，使用此接口取消订阅。 <br>调用此接口后，之前通过subscribeCompass注册的回调函数将不再被触发。需先调用subscribeCompass订阅后，再调用此接口取消订阅，否则无效果。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ORIENTATION](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback?: Callback&lt;OrientationResponse&gt;)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeCompass(): void--><!--Device-Sensor-static unsubscribeCompass(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeDeviceOrientation

```TypeScript
static unsubscribeDeviceOrientation(): void
```

取消订阅设备方向传感器数据。调用后，设备方向传感器的回调函数将不再触发。 <br>当开发者不再需要设备方向数据时，使用此接口取消订阅。 <br>调用此接口后，之前通过subscribeDeviceOrientation注册的回调函数将不再被触发。需先调用subscribeDeviceOrientation订阅后，再调用此接口取消订阅，否则无效果。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [ORIENTATION](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) > 替代。 **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback?: Callback&lt;OrientationResponse&gt;)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeDeviceOrientation(): void--><!--Device-Sensor-static unsubscribeDeviceOrientation(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeGyroscope

```TypeScript
static unsubscribeGyroscope(): void
```

取消订阅陀螺仪传感器数据。调用后，陀螺仪传感器的回调函数将不再触发。 <br>当开发者不再需要陀螺仪数据时，使用此接口取消订阅。 <br>调用此接口后，之前通过subscribeGyroscope注册的回调函数将不再被触发。需先调用subscribeGyroscope订阅后，再调用此接口取消订阅，否则无效果。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [GYROSCOPE](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) > 替代。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback?: Callback&lt;GyroscopeResponse&gt;)

**需要权限：** ohos.permission.GYROSCOPE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeGyroscope(): void--><!--Device-Sensor-static unsubscribeGyroscope(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeHeartRate

```TypeScript
static unsubscribeHeartRate(): void
```

取消订阅心率传感器数据。调用后，心率传感器的回调函数将不再触发。 <br>当开发者不再需要心率数据时，使用此接口取消订阅。 <br>调用此接口后，之前通过subscribeHeartRate注册的回调函数将不再被触发。需先调用subscribeHeartRate订阅后，再调用此接口取消订阅，否则无效果。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [HEART_RATE](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback?: Callback&lt;HeartRateResponse&gt;)

**需要权限：** ohos.permission.READ_HEALTH_DATA

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeHeartRate(): void--><!--Device-Sensor-static unsubscribeHeartRate(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeLight

```TypeScript
static unsubscribeLight(): void
```

取消订阅环境光传感器数据。调用后，环境光传感器的回调函数将不再触发。 <br>当开发者不再需要环境光线数据时，使用此接口取消订阅。 <br>调用此接口后，之前通过subscribeLight注册的回调函数将不再被触发。需先调用subscribeLight订阅后，再调用此接口取消订阅，否则无效果。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [AMBIENT_LIGHT](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) > 替代。 **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback?: Callback&lt;LightResponse&gt;)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeLight(): void--><!--Device-Sensor-static unsubscribeLight(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeOnBodyState

```TypeScript
static unsubscribeOnBodyState(): void
```

取消订阅设备佩戴状态。调用后，佩戴状态的回调函数将不再触发。 <br>当开发者不再需要佩戴状态数据时，使用此接口取消订阅。 <br>调用此接口后，之前通过subscribeOnBodyState注册的回调函数将不再被触发。需先调用subscribeOnBodyState订阅后，再调用此接口取消订阅，否则无效果。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [WEAR_DETECTION](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback?: Callback&lt;WearDetectionResponse&gt;)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeOnBodyState(): void--><!--Device-Sensor-static unsubscribeOnBodyState(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeProximity

```TypeScript
static unsubscribeProximity(): void
```

取消订阅距离传感器数据。调用后，距离传感器的回调函数将不再触发。 <br>当开发者不再需要距离感应数据时，使用此接口取消订阅。 <br>调用此接口后，之前通过subscribeProximity注册的回调函数将不再被触发。需先调用subscribeProximity订阅后，再调用此接口取消订阅，否则无效果。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [PROXIMITY](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) > 替代。 **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [PROXIMITY](arkts-sensorservice-sensor-sensorid-e.md#proximity)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeProximity(): void--><!--Device-Sensor-static unsubscribeProximity(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## unsubscribeStepCounter

```TypeScript
static unsubscribeStepCounter(): void
```

取消订阅计步传感器数据。调用后，计步传感器的回调函数将不再触发。 <br>当开发者不再需要计步数据时，使用此接口取消订阅。 <br>调用此接口后，之前通过subscribeStepCounter注册的回调函数将不再被触发。需先调用subscribeStepCounter订阅后，再调用此接口取消订阅，否则无效果。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [PEDOMETER](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) > 替代。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor)(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback?: Callback&lt;PedometerResponse&gt;)

**需要权限：** ohos.permission.ACTIVITY_MOTION

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Sensor-static unsubscribeStepCounter(): void--><!--Device-Sensor-static unsubscribeStepCounter(): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

