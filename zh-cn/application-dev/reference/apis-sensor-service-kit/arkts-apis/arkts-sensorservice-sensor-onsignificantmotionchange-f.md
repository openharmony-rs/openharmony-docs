# onSignificantMotionChange

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## onSignificantMotionChange

```TypeScript
function onSignificantMotionChange(callback: Callback<SignificantMotionResponse>, options?: Options): void
```

Subscribe to significant motion sensor data, {@code SensorId.SIGNIFICANT_MOTION}.

**起始版本：** 23

<!--Device-sensor-function onSignificantMotionChange(callback: Callback<SignificantMotionResponse>, options?: Options): void--><!--Device-sensor-function onSignificantMotionChange(callback: Callback<SignificantMotionResponse>, options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | 是 | callback significant motion data. |
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
  sensor.onSignificantMotionChange((data: sensor.SignificantMotionResponse) => {
    console.info('Succeeded in invoking onSignificantMotionChange. Scalar data: ' + data.scalar);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offSignificantMotionChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onSignificantMotionChange. Code: ${e.code}, message: ${e.message}`);
}
```

