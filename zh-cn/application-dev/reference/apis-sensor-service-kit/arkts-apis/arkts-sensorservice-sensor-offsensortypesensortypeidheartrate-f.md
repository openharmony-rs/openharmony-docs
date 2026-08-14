# off_SensorType.SENSOR_TYPE_ID_HEART_RATE

## off_SensorType.SENSOR_TYPE_ID_HEART_RATE

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback?: Callback<HeartRateResponse>): void
```

取消订阅心率传感器数据。off取消订阅必须与on订阅成对出现。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [off](arkts-sensorservice-sensor-offsensoridcolor-f-sys.md#off_SensorId.COLOR)(type: SensorId.HEART_RATE, callback?: Callback&lt;HeartRateResponse&gt;)

**需要权限：** ohos.permission.HEALTH_DATA

<!--Device-sensor-function off(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback?: Callback<HeartRateResponse>): void--><!--Device-sensor-function off(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback?: Callback<HeartRateResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HEART_RATE | 是 | 要取消订阅的心率传感器类型为SENSOR_TYPE_ID_HEART_RATE。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;HeartRateResponse&gt; | 否 | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

