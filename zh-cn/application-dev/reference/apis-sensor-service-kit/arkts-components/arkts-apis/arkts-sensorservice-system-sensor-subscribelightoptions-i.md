# SubscribeLightOptions

用于设置环境光传感器订阅的参数，包括回调函数。

**设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [AMBIENT_LIGHT](arkts-sensorservice-sensor-sensorid-e.md#ambient_light)

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## 导入模块

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。回调参数为(data: string, code: number)，其中data为错误信息，code为错误码。不填写时，接口调用失败无回调通知。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-on-f.md)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success: (data: LightResponse) => void
```

光线感应数据改变后的回调函数，回调参数为LightResponse对象。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-on-f.md)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [LightResponse](arkts-sensorservice-system-sensor-lightresponse-i.md) | 是 |  |
