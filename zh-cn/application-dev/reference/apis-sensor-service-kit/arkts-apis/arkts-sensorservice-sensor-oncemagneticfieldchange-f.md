# onceMagneticFieldChange

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## onceMagneticFieldChange

```TypeScript
function onceMagneticFieldChange(callback: Callback<MagneticFieldResponse>): void
```

Subscribe to magnetic field sensor data once, {@code SensorId.MAGNETIC_FIELD}.

**起始版本：** 23

<!--Device-sensor-function onceMagneticFieldChange(callback: Callback<MagneticFieldResponse>): void--><!--Device-sensor-function onceMagneticFieldChange(callback: Callback<MagneticFieldResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | 是 | callback magnetic field data. |

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
  sensor.onceMagneticFieldChange((data: sensor.MagneticFieldResponse) => {
    console.info('Succeeded in invoking onceMagneticFieldChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onceMagneticFieldChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onceMagneticFieldChange. Z-coordinate component: ' + data.z);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceMagneticFieldChange. Code: ${e.code}, message: ${e.message}`);
}
```

