# once_SensorType.SENSOR_TYPE_ID_PROXIMITY

## once_SensorType.SENSOR_TYPE_ID_PROXIMITY

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback<ProximityResponse>): void
```

监听接近光传感器数据变化一次。适用于仅需一次性获取当前接近光数据的场景。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.PROXIMITY] > once > 替代。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 9

**替代接口：** once(type: SensorId.PROXIMITY, callback: Callback&lt;ProximityResponse&gt;)

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback<ProximityResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback<ProximityResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_PROXIMITY | 是 | 接近光传感器类型为SENSOR_TYPE_ID_PROXIMITY。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;ProximityResponse&gt; | 是 | 注册一次接近光传感器的回调函数，上报的数据类型为ProximityResponse。 |

