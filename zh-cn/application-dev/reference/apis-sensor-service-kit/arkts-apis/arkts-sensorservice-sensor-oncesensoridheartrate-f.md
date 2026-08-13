# once_SensorId.HEART_RATE

## once_SensorId.HEART_RATE

```TypeScript
function once(type: SensorId.HEART_RATE, callback: Callback<HeartRateResponse>): void
```

获取一次心率传感器数据。适用于仅需一次性获取当前心率值的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_HEALTH_DATA

<!--Device-sensor-function once(type: SensorId.HEART_RATE, callback: Callback<HeartRateResponse>): void--><!--Device-sensor-function once(type: SensorId.HEART_RATE, callback: Callback<HeartRateResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HEART_RATE | 是 | 传感器类型，该值固定为SensorId.HEART_RATE。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;HeartRateResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为HeartRateResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.HEART_RATE, (data: sensor.HeartRateResponse) => {
    console.info('Succeeded in invoking once. Heart rate: ' + data.heartRate);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

