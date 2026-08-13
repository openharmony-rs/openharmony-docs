# once_SensorId.GRAVITY

## once_SensorId.GRAVITY

```TypeScript
function once(type: SensorId.GRAVITY, callback: Callback<GravityResponse>): void
```

获取一次重力传感器数据。适用于仅需一次性获取当前重力分量的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-sensor-function once(type: SensorId.GRAVITY, callback: Callback<GravityResponse>): void--><!--Device-sensor-function once(type: SensorId.GRAVITY, callback: Callback<GravityResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GRAVITY | 是 | 传感器类型，该值固定为SensorId.GRAVITY。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为GravityResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |

## 示例

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.GRAVITY, (data: sensor.GravityResponse) => {
    console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

