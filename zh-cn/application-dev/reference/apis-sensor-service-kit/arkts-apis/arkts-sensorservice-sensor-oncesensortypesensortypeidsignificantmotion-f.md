# once_SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## once_SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback<SignificantMotionResponse>): void
```

监听有效运动传感器的数据变化一次。适用于仅需一次性获取当前有效运动数据的场景。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.SIGNIFICANT_MOTION] > once > 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** once(type: SensorId.SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;)

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback<SignificantMotionResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback<SignificantMotionResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION | 是 | 有效运动传感器类型为SENSOR_TYPE_ID_SIGNIFICANT_MOTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | 是 | 注册一次有效运动传感器的回调函数，上报的数据类型为SignificantMotionResponse。 |

