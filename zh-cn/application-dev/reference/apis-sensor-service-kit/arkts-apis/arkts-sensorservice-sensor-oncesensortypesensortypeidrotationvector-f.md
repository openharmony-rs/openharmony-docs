# once_SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR

## once_SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback<RotationVectorResponse>): void
```

监听旋转矢量传感器数据变化一次。适用于仅需一次性获取当前旋转矢量数据的场景。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** once(type: SensorId.ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;)

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback<RotationVectorResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback<RotationVectorResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR | 是 | 旋转矢量传感器类型为SENSOR_TYPE_ID_ROTATION_VECTOR。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | 是 | 注册一次旋转矢量传感器的回调函数，上报的数据类型为RotationVectorResponse。 |

