# OnBodyStateResponse

设备佩戴状态的响应对象，包含设备是否已佩戴的状态数据。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)

<!--Device-unnamed-export interface OnBodyStateResponse--><!--Device-unnamed-export interface OnBodyStateResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## 导入模块

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## value

```TypeScript
value: boolean
```

是否已佩戴设备。取值说明：true表示已佩戴，false表示未佩戴。

**类型：** boolean

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [value](arkts-sensorservice-sensor-weardetectionresponse-i.md#value)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-OnBodyStateResponse-value: boolean--><!--Device-OnBodyStateResponse-value: boolean-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

