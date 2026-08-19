# GyroscopeResponse

陀螺仪传感器数据变化后的回调函数的响应对象，包含设备在x、y、z三轴方向的旋转角速度数据。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [GyroscopeResponse](arkts-sensorservice-sensor-gyroscoperesponse-i.md)

**需要权限：** ohos.permission.GYROSCOPE

<!--Device-unnamed-export interface GyroscopeResponse--><!--Device-unnamed-export interface GyroscopeResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## 导入模块

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## x

```TypeScript
x: number
```

x轴的旋转角速度。单位：rad/s（弧度/秒）。取值范围：取值为实际上报物理量，由硬件传感器决定。

**类型：** number

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [x](arkts-sensorservice-sensor-gyroscoperesponse-i.md#x)

**需要权限：** ohos.permission.GYROSCOPE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GyroscopeResponse-x: number--><!--Device-GyroscopeResponse-x: number-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## y

```TypeScript
y: number
```

y轴的旋转角速度。单位：rad/s（弧度/秒）。取值范围：取值为实际上报物理量，由硬件传感器决定。

**类型：** number

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [y](arkts-sensorservice-sensor-gyroscoperesponse-i.md#y)

**需要权限：** ohos.permission.GYROSCOPE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GyroscopeResponse-y: number--><!--Device-GyroscopeResponse-y: number-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## z

```TypeScript
z: number
```

z轴的旋转角速度。单位：rad/s（弧度/秒）。取值范围：取值为实际上报物理量，由硬件传感器决定。

**类型：** number

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [z](arkts-sensorservice-sensor-gyroscoperesponse-i.md#z)

**需要权限：** ohos.permission.GYROSCOPE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GyroscopeResponse-z: number--><!--Device-GyroscopeResponse-z: number-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

