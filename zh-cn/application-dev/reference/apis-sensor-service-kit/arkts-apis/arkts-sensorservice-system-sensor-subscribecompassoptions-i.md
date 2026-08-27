# SubscribeCompassOptions

用于设置罗盘传感器订阅的参数，包括回调函数。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [ORIENTATION](arkts-sensorservice-sensor-sensorid-e.md#orientation)

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

**替代接口：** [on](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success: (data: CompassResponse) => void
```

罗盘数据改变后触发的回调函数，回调参数为CompassResponse对象。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [on](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [CompassResponse](arkts-sensorservice-system-sensor-compassresponse-i.md) | 是 |  |
