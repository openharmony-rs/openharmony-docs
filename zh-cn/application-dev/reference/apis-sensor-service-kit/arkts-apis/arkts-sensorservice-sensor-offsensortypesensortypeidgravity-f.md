# off_SensorType.SENSOR_TYPE_ID_GRAVITY

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## off_SensorType.SENSOR_TYPE_ID_GRAVITY

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback?: Callback<GravityResponse>): void
```

取消订阅重力传感器数据。off取消订阅必须与on订阅成对出现。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.GRAVITY] > [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor) > 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_sensoridcolor)(type: SensorId.GRAVITY, callback?: Callback&lt;GravityResponse&gt;)

<!--Device-sensor-function off(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback?: Callback<GravityResponse>): void--><!--Device-sensor-function off(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback?: Callback<GravityResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_GRAVITY | 是 | 要取消订阅的重力传感器类型为SENSOR_TYPE_ID_GRAVITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

