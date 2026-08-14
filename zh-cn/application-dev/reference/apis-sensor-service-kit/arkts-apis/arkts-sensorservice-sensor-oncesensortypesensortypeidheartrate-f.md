# once_SensorType.SENSOR_TYPE_ID_HEART_RATE

## once_SensorType.SENSOR_TYPE_ID_HEART_RATE

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback<HeartRateResponse>): void
```

监听心率传感器数据变化一次。适用于仅需一次性获取当前心率数据的场景。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** once(type: SensorId.HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;)

**需要权限：** ohos.permission.HEART_RATE

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback<HeartRateResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback<HeartRateResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HEART_RATE | 是 | 心率传感器类型为SENSOR_TYPE_ID_HEART_RATE。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;HeartRateResponse&gt; | 是 | 注册一次心率传感器的回调函数，上报的数据类型为HeartRateResponse。 |

