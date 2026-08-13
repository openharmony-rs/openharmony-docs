# onceWearDetectionChange

## onceWearDetectionChange

```TypeScript
function onceWearDetectionChange(callback: Callback<WearDetectionResponse>): void
```

Subscribe to wear detection sensor data once, {@code SensorId.WEAR_DETECTION}.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-function onceWearDetectionChange(callback: Callback<WearDetectionResponse>): void--><!--Device-sensor-function onceWearDetectionChange(callback: Callback<WearDetectionResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | 是 | callback wear detection data. |

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
  sensor.onceWearDetectionChange((data: sensor.WearDetectionResponse) => {
    console.info('Succeeded in invoking onceWearDetectionChange. Wear status: ' + data.value);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceWearDetectionChange. Code: ${e.code}, message: ${e.message}`);
}
```

