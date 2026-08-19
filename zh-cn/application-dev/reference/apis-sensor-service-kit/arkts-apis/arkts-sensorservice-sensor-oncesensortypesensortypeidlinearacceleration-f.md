# once_SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## once_SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback: Callback<LinearAccelerometerResponse>): void
```

监听线性加速度传感器数据变化一次。适用于仅需一次性获取当前线性加速度数据的场景。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.LINEAR_ACCELEROMETER] > once > 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** once(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback&lt;LinearAccelerometerResponse&gt;)

**需要权限：** ohos.permission.ACCELEROMETER

<!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback: Callback<LinearAccelerometerResponse>): void--><!--Device-sensor-function once(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback: Callback<LinearAccelerometerResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION | 是 | 线性加速度传感器类型为SENSOR_TYPE_ID_LINEAR_ACCELERATION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | 是 | 注册一次线性加速度传感器的回调函数， 上报的数据类型为LinearAccelerometerResponse。 |

