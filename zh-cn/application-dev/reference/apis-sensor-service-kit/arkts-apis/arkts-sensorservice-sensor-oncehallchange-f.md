# onceHallChange

## onceHallChange

```TypeScript
function onceHallChange(callback: Callback<HallResponse>): void
```

Subscribe to hall sensor data once, {@code SensorId.HALL}.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-function onceHallChange(callback: Callback<HallResponse>): void--><!--Device-sensor-function onceHallChange(callback: Callback<HallResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | 是 | callback hall data. |

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
  sensor.onceHallChange((data: sensor.HallResponse) => {
    console.info('Succeeded in invoking onceHallChange. Status: ' + data.status);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceHallChange. Code: ${e.code}, message: ${e.message}`);
}
```

