# once_SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## once_SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback: Callback<AccelerometerUncalibratedResponse>): void
```

监听未校准加速度传感器的数据变化一次。适用于仅需一次性获取当前未校准加速度数据的场景。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ACCELEROMETER_UNCALIBRATED] > once > 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** once(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback&lt;AccelerometerUncalibratedResponse&gt;)

**需要权限：** ohos.permission.ACCELEROMETER

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback: Callback<AccelerometerUncalibratedResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback: Callback<AccelerometerUncalibratedResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED | 是 | 未校准加速度传感器类型为SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | 是 | 注册一次未校准加速度传感器的回调函数，上报的数据类型为AccelerometerUncalibratedResponse。 |

