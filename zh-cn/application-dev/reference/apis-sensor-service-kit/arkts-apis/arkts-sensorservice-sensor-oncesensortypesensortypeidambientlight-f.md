# once_SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## once_SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback<LightResponse>): void
```

监听环境光传感器数据变化一次。适用于仅需一次性获取当前环境光数据的场景。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.AMBIENT_LIGHT] > once > 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** once(type: SensorId.AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;)

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback<LightResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback<LightResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT | 是 | 环境光传感器类型为SENSOR_TYPE_ID_AMBIENT_LIGHT。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;LightResponse&gt; | 是 | 注册一次环境光传感器的回调函数，上报的数据类型为LightResponse。 |

