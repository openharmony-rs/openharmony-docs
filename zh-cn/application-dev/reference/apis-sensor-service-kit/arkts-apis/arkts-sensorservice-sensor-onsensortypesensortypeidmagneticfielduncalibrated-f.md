# on_SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED

## on_SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback<MagneticFieldUncalibratedResponse>,
    options?: Options): void
```

监听未校准磁场传感器的数据变化。适用于需要获取包含偏差校准数据的磁场原始数据的场景。如果多次调用该接口，仅最后一次调用生效。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_SensorId.COLOR)(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;, options?: Options)

<!--Device-sensor-function on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback<MagneticFieldUncalibratedResponse>,    options?: Options): void--><!--Device-sensor-function on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback<MagneticFieldUncalibratedResponse>,    options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | 是 | 要订阅的未校准磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | 是 | 注册未校准磁场传感器的回调函数，上报的数据类型为MagneticFieldUncalibratedResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

