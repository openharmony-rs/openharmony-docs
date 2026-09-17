# ProximityResponse

距离感应数据改变后的回调函数的响应对象，包含可见物体相对于设备显示屏的接近或远离状态数据。

**设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [ProximityResponse](arkts-sensorservice-sensor-proximityresponse-i.md)

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## 导入模块

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## distance

```TypeScript
distance: number
```

可见物体相对于设备显示屏的接近或远离状态。取值说明：0表示物体接近屏幕（近状态），大于0表示物体远离屏幕（远状态）。具体远状态数值由硬件传感器决定。

**类型：** number

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [distance](arkts-sensorservice-sensor-proximityresponse-i.md#distance)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Sensors.Sensor.Lite
