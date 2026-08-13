# on_SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR

## on_SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback<RotationVectorResponse>,
    options?: Options): void
```

监听旋转矢量传感器的数据变化。适用于需要感知设备三维空间旋转状态的场景。如果多次调用该接口，仅最后一次调用生效。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_SensorId.COLOR)(type: SensorId.ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;, options?: Options)

<!--Device-sensor-function on(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback<RotationVectorResponse>,    options?: Options): void--><!--Device-sensor-function on(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback<RotationVectorResponse>,    options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR | 是 | 要订阅的旋转矢量传感器类型为SENSOR_TYPE_ID_ROTATION_VECTOR。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | 是 | 注册旋转矢量传感器的回调函数，上报的数据类型为RotationVectorResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

