# once_SensorType.SENSOR_TYPE_ID_ORIENTATION

## once_SensorType.SENSOR_TYPE_ID_ORIENTATION

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback<OrientationResponse>): void
```

监听方向传感器数据变化一次。适用于仅需一次性获取当前方向数据的场景。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** once(type: SensorId.ORIENTATION, callback: Callback&lt;OrientationResponse&gt;)

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback<OrientationResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback<OrientationResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ORIENTATION | 是 | 方向传感器类型为SENSOR_TYPE_ID_ORIENTATION。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | 是 | 注册一次方向传感器的回调函数，上报的数据类型为OrientationResponse。 |

