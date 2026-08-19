# once_SensorType.SENSOR_TYPE_ID_GRAVITY

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## once_SensorType.SENSOR_TYPE_ID_GRAVITY

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback<GravityResponse>): void
```

监听重力传感器的数据变化一次。适用于仅需一次性获取当前重力数据的场景。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.GRAVITY] > once > 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** once(type: SensorId.GRAVITY, callback: Callback&lt;GravityResponse&gt;)

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback<GravityResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback<GravityResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_GRAVITY | 是 | 重力传感器类型为SENSOR_TYPE_ID_GRAVITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | 是 | 注册一次重力传感器的回调函数，上报的数据类型为GravityResponse。 |

