# CompassResponse

罗盘数据改变后的回调函数的响应对象，包含设备面对的方向度数。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## 导入模块

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## direction

```TypeScript
direction: number
```

设备面对的方向度数。单位：°（度）。取值范围：[0, 360)，0表示朝北。取值为实际上报物理量。

**类型：** number

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [alpha](arkts-sensorservice-sensor-orientationresponse-i.md#alpha)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Sensors.Sensor.Lite
