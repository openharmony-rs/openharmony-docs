# onLinearAccelerometerChange

## onLinearAccelerometerChange

```TypeScript
function onLinearAccelerometerChange(callback: Callback<LinearAccelerometerResponse>, options?: Options): void
```

Subscribe to linear acceleration sensor data, {@code SensorId.LINEAR_ACCELEROMETER}.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCELEROMETER

<!--Device-sensor-function onLinearAccelerometerChange(callback: Callback<LinearAccelerometerResponse>, options?: Options): void--><!--Device-sensor-function onLinearAccelerometerChange(callback: Callback<LinearAccelerometerResponse>, options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | 是 | callback linear accelerometer data. |
| options | Options | 否 | Optional parameters specifying the interval at which sensor data is reported, &lt;br&gt; {@code Options}. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onLinearAccelerometerChange((data: sensor.LinearAccelerometerResponse) => {
    console.info('Succeeded in invoking onLinearAccelerometerChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onLinearAccelerometerChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onLinearAccelerometerChange. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offLinearAccelerometerChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onLinearAccelerometerChange. Code: ${e.code}, message: ${e.message}`);
}
```

