# once_SensorType.SENSOR_TYPE_ID_HALL

## once_SensorType.SENSOR_TYPE_ID_HALL

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback<HallResponse>): void
```

监听霍尔传感器数据变化一次。适用于仅需一次性获取当前霍尔数据的场景。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** once(type: SensorId.HALL, callback: Callback&lt;HallResponse&gt;)

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback<HallResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback<HallResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HALL | 是 | 霍尔传感器类型为SENSOR_TYPE_ID_HALL。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | 是 | 注册一次霍尔传感器的回调函数，上报的数据类型为HallResponse。 |

