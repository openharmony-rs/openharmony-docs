# onHallChange

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## onHallChange

```TypeScript
function onHallChange(callback: Callback<HallResponse>, options?: Options): void
```

Subscribe to hall sensor data, {@code SensorId.HALL}.

**起始版本：** 23

<!--Device-sensor-function onHallChange(callback: Callback<HallResponse>, options?: Options): void--><!--Device-sensor-function onHallChange(callback: Callback<HallResponse>, options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | 是 | callback hall data. |
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
  sensor.onHallChange((data: sensor.HallResponse) => {
    console.info('Succeeded in invoking onHallChange. Hall status: ' + data.status);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offHallChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onHallChange. Code: ${e.code}, message: ${e.message}`);
}
```

