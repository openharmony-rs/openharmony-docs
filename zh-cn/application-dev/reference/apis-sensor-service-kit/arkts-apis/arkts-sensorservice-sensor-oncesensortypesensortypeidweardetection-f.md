# once_SensorType.SENSOR_TYPE_ID_WEAR_DETECTION

## once_SensorType.SENSOR_TYPE_ID_WEAR_DETECTION

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback<WearDetectionResponse>): void
```

监听所佩戴的检测传感器的数据变化一次。适用于仅需一次性获取当前佩戴检测数据的场景。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** once(type: SensorId.WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;)

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback<WearDetectionResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback<WearDetectionResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_WEAR_DETECTION | 是 | 佩戴检测传感器类型为SENSOR_TYPE_ID_WEAR_DETECTION。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | 是 | 注册一次穿戴检测传感器的回调函数，上报的数据类型为WearDetectionResponse。 |

