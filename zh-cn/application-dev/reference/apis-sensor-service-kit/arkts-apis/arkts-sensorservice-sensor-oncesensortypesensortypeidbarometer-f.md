# once_SensorType.SENSOR_TYPE_ID_BAROMETER

## once_SensorType.SENSOR_TYPE_ID_BAROMETER

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback<BarometerResponse>): void
```

监听气压计传感器数据变化一次。适用于仅需一次性获取当前气压数据的场景。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** once(type: SensorId.BAROMETER, callback: Callback&lt;BarometerResponse&gt;)

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback<BarometerResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback<BarometerResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_BAROMETER | 是 | 气压计传感器类型为SENSOR_TYPE_ID_BAROMETER。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;BarometerResponse&gt; | 是 | 注册一次气压计传感器的回调函数，上报的数据类型为BarometerResponse。 |

