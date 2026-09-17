# GetOnBodyStateOptions

获取传感器所在设备佩戴状态时的参数，包括回调函数。此接口为一次性获取，不会持续监听状态变化。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [WEAR_DETECTION](arkts-sensorservice-sensor-sensorid-e.md#wear_detection)

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## 导入模块

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。无论调用成功或失败，此回调都会被执行。不填写时，接口调用结束无回调通知。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [once](arkts-sensorservice-sensor-once-f.md)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。回调参数为(data: string, code: number)，其中data为错误信息，code为错误码。不填写时，接口调用失败无回调通知。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [once](arkts-sensorservice-sensor-once-f.md)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success: (data: OnBodyStateResponse) => void
```

接口调用成功的回调函数，回调参数为OnBodyStateResponse对象。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [once](arkts-sensorservice-sensor-once-f.md)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Sensors.Sensor.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [OnBodyStateResponse](arkts-sensorservice-system-sensor-onbodystateresponse-i.md) | 是 |  |
