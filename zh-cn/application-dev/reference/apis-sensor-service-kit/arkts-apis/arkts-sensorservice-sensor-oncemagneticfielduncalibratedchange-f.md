# onceMagneticFieldUncalibratedChange

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## onceMagneticFieldUncalibratedChange

```TypeScript
function onceMagneticFieldUncalibratedChange(callback: Callback<MagneticFieldUncalibratedResponse>): void
```

Subscribe to uncalibrated magnetic field sensor data once, {@code SensorId.MAGNETIC_FIELD_UNCALIBRATED}.

**起始版本：** 23

<!--Device-sensor-function onceMagneticFieldUncalibratedChange(callback: Callback<MagneticFieldUncalibratedResponse>): void--><!--Device-sensor-function onceMagneticFieldUncalibratedChange(callback: Callback<MagneticFieldUncalibratedResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | 是 | callback uncalibrated magnetic field data. |

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
  sensor.onceMagneticFieldUncalibratedChange((data: sensor.MagneticFieldUncalibratedResponse) => {
    console.info('Succeeded in invoking onceMagneticFieldUncalibratedChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onceMagneticFieldUncalibratedChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onceMagneticFieldUncalibratedChange. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking onceMagneticFieldUncalibratedChange. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking onceMagneticFieldUncalibratedChange. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking onceMagneticFieldUncalibratedChange. Z-coordinate bias: ' + data.biasZ);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceMagneticFieldUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
}
```

