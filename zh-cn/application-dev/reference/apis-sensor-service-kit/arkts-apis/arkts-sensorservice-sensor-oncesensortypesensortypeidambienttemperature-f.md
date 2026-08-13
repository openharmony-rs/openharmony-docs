# once_SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE

## once_SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback<AmbientTemperatureResponse>): void
```

监听环境温度传感器数据变化一次。适用于仅需一次性获取当前环境温度数据的场景。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** once(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback&lt;AmbientTemperatureResponse&gt;)

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback<AmbientTemperatureResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback<AmbientTemperatureResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE | 是 | 环境温度传感器类型为SENSOR_TYPE_ID_AMBIENT_TEMPERATURE。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | 是 | 注册一次环境温度传感器的回调函数，上报的数据类型为AmbientTemperatureResponse。 |

