# once_SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT

## once_SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback<LightResponse>): void
```

监听环境光传感器数据变化一次。适用于仅需一次性获取当前环境光数据的场景。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** once(type: SensorId.AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;)

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback<LightResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback<LightResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT | 是 | 环境光传感器类型为SENSOR_TYPE_ID_AMBIENT_LIGHT。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;LightResponse&gt; | 是 | 注册一次环境光传感器的回调函数，上报的数据类型为LightResponse。 |

