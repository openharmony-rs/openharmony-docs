# on_SensorType.SENSOR_TYPE_ID_ORIENTATION

## on_SensorType.SENSOR_TYPE_ID_ORIENTATION

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback<OrientationResponse>,
    options?: Options): void
```

监听方向传感器的数据变化。适用于需要感知设备姿态方向的场景。如果多次调用该接口，仅最后一次调用生效。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_SensorId.COLOR)(type: SensorId.ORIENTATION, callback: Callback&lt;OrientationResponse&gt;, options?: Options)

<!--Device-sensor-function on(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback<OrientationResponse>,    options?: Options): void--><!--Device-sensor-function on(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback<OrientationResponse>,    options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ORIENTATION | 是 | 要订阅的方向传感器类型为SENSOR_TYPE_ID_ORIENTATION。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | 是 | 注册方向传感器的回调函数，上报的数据类型为OrientationResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

