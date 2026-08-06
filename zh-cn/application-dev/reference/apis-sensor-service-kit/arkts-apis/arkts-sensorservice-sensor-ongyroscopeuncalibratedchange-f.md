# onGyroscopeUncalibratedChange

## onGyroscopeUncalibratedChange

```TypeScript
function onGyroscopeUncalibratedChange(callback: Callback<GyroscopeUncalibratedResponse>, options?: Options): void
```

Subscribe to uncalibrated gyroscope sensor data, {@code SensorId.GYROSCOPE\_UNCALIBRATED}.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.GYROSCOPE

<!--Device-sensor-function onGyroscopeUncalibratedChange(callback: Callback<GyroscopeUncalibratedResponse>, options?: Options): void--><!--Device-sensor-function onGyroscopeUncalibratedChange(callback: Callback<GyroscopeUncalibratedResponse>, options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;GyroscopeUncalibratedResponse&gt; | 是 | callback uncalibrated gyroscope data. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Optional parameters specifying the interval at which sensor data is reported,\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ {@code Options}. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onGyroscopeUncalibratedChange((data: sensor.GyroscopeUncalibratedResponse) => {
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. Z-coordinate bias: ' + data.biasZ);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offGyroscopeUncalibratedChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onGyroscopeUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
}
```

