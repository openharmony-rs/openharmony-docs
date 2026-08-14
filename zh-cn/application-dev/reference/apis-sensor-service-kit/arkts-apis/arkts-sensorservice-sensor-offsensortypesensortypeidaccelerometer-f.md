# off_SensorType.SENSOR_TYPE_ID_ACCELEROMETER

## off_SensorType.SENSOR_TYPE_ID_ACCELEROMETER

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback?: Callback<AccelerometerResponse>): void
```

取消订阅加速度传感器数据。off取消订阅必须与on订阅成对出现。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_SensorId.COLOR)(type: SensorId.ACCELEROMETER, callback?: Callback&lt;AccelerometerResponse&gt;)

**需要权限：** ohos.permission.ACCELEROMETER

<!--Device-sensor-function off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback?: Callback<AccelerometerResponse>): void--><!--Device-sensor-function off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback?: Callback<AccelerometerResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ACCELEROMETER | 是 | 要取消订阅的加速度传感器类型为SENSOR_TYPE_ID_ACCELEROMETER。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;AccelerometerResponse&gt; | 否 | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

