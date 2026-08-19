# on_SensorId.MAGNETIC_FIELD

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## on_SensorId.MAGNETIC_FIELD

```TypeScript
function on(type: SensorId.MAGNETIC_FIELD, callback: Callback<MagneticFieldResponse>,
    options?: Options): void
```

订阅地磁传感器数据。地磁传感器用于测量设备周围的磁场强度在X、Y、Z三个方向上的分量，适用于指南针、方向检测、金属检测等场景。调用后，系统会按设定频率通过callback持续上报磁场分量数据。

**起始版本：** 9

<!--Device-sensor-function on(type: SensorId.MAGNETIC_FIELD, callback: Callback<MagneticFieldResponse>,    options?: Options): void--><!--Device-sensor-function on(type: SensorId.MAGNETIC_FIELD, callback: Callback<MagneticFieldResponse>,    options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.MAGNETIC_FIELD | 是 | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为MagneticFieldResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; <br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.MAGNETIC_FIELD, (data: sensor.MagneticFieldResponse) => {
    console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.MAGNETIC_FIELD);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```

