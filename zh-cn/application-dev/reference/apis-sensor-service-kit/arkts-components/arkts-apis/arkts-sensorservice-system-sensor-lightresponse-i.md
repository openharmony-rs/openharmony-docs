# LightResponse

光线感应数据改变后的回调函数的响应对象，包含环境光线强度数据。

**设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [LightResponse](arkts-sensorservice-sensor-lightresponse-i.md)

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## 导入模块

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## intensity

```TypeScript
intensity: number
```

环境光线强度。单位：lux（勒克斯）。取值范围：取值为实际上报物理量，由硬件传感器决定。

**类型：** number

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [intensity](arkts-sensorservice-sensor-lightresponse-i.md#intensity)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Sensors.Sensor.Lite
