# onGyroscopeChange

## onGyroscopeChange

```TypeScript
function onGyroscopeChange(callback: Callback<GyroscopeResponse>, options?: Options): void
```

Subscribe to gyroscope sensor data, {@code SensorId.GYROSCOPE}.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GYROSCOPE

<!--Device-sensor-function onGyroscopeChange(callback: Callback<GyroscopeResponse>, options?: Options): void--><!--Device-sensor-function onGyroscopeChange(callback: Callback<GyroscopeResponse>, options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;GyroscopeResponse&gt; | 是 | callback gyroscope data. |
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
  sensor.onGyroscopeChange((data: sensor.GyroscopeResponse) => {
    console.info('Succeeded in invoking onGyroscopeChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onGyroscopeChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onGyroscopeChange. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offGyroscopeChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onGyroscopeChange. Code: ${e.code}, message: ${e.message}`);
}
```

