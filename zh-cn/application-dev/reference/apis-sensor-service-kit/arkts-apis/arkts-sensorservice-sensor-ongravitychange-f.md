# onGravityChange

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## onGravityChange

```TypeScript
function onGravityChange(callback: Callback<GravityResponse>, options?: Options): void
```

Subscribe to gravity sensor data, {@code SensorId.GRAVITY}.

**起始版本：** 23

<!--Device-sensor-function onGravityChange(callback: Callback<GravityResponse>, options?: Options): void--><!--Device-sensor-function onGravityChange(callback: Callback<GravityResponse>, options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | 是 | callback gravity data. |
| options | Options | 否 | Optional parameters specifying the interval at which sensor data is reported, <br> {@code Options}. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; <br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onGravityChange((data: sensor.GravityResponse) => {
    console.info('Succeeded in invoking onGravityChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onGravityChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onGravityChange. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offGravityChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onGravityChange. Code: ${e.code}, message: ${e.message}`);
}
```

