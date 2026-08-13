# on_SensorType.SENSOR_TYPE_ID_PEDOMETER

## on_SensorType.SENSOR_TYPE_ID_PEDOMETER

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback<PedometerResponse>,
    options?: Options): void
```

监听计步传感器的数据变化。适用于需要获取用户步数数据的场景。如果多次调用该接口，仅最后一次调用生效。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [on](arkts-sensorservice-sensor-onsensoridcolor-f-sys.md#on_SensorId.COLOR)(type: SensorId.PEDOMETER, callback: Callback&lt;PedometerResponse&gt;, options?: Options)

**需要权限：** ohos.permission.ACTIVITY_MOTION

<!--Device-sensor-function on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback<PedometerResponse>,    options?: Options): void--><!--Device-sensor-function on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback<PedometerResponse>,    options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_PEDOMETER | 是 | 要订阅的计步传感器类型为SENSOR_TYPE_ID_PEDOMETER。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | 是 | 注册计步传感器的回调函数，上报的数据类型为PedometerResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

