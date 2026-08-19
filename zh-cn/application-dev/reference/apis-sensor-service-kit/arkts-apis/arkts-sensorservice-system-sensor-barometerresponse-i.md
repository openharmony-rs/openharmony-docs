# BarometerResponse

气压计传感器数据改变后的回调函数的响应对象，包含气压值数据。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [BarometerResponse](arkts-sensorservice-sensor-barometerresponse-i.md)

<!--Device-unnamed-export interface BarometerResponse--><!--Device-unnamed-export interface BarometerResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## 导入模块

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## pressure

```TypeScript
pressure: number
```

气压值。单位：Pa（帕斯卡）。取值范围：取值为实际上报物理量，由硬件传感器决定。标准大气压约为101325 Pa。

**类型：** number

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [pressure](arkts-sensorservice-sensor-barometerresponse-i.md#pressure)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-BarometerResponse-pressure: number--><!--Device-BarometerResponse-pressure: number-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

