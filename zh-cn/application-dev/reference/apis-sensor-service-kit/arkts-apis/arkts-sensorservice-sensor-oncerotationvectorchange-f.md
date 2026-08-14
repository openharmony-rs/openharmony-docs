# onceRotationVectorChange

## onceRotationVectorChange

```TypeScript
function onceRotationVectorChange(callback: Callback<RotationVectorResponse>): void
```

Subscribe to rotation vector sensor data once, {@code SensorId.ROTATION_VECTOR}.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-function onceRotationVectorChange(callback: Callback<RotationVectorResponse>): void--><!--Device-sensor-function onceRotationVectorChange(callback: Callback<RotationVectorResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | 是 | callback rotation vector data. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceRotationVectorChange((data: sensor.RotationVectorResponse) => {
    console.info('Succeeded in invoking onceRotationVectorChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onceRotationVectorChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onceRotationVectorChange. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking onceRotationVectorChange. Scalar quantity: ' + data.w);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceRotationVectorChange. Code: ${e.code}, message: ${e.message}`);
}
```

