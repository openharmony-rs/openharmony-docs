# getSingleSensorSync

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getSingleSensorSync

```TypeScript
function getSingleSensorSync(type: SensorId): Sensor
```

获取指定类型的传感器信息，使用同步方式返回结果。

**起始版本：** 23

<!--Device-sensor-function getSingleSensorSync(type: SensorId): Sensor--><!--Device-sensor-function getSingleSensorSync(type: SensorId): Sensor-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SensorId](arkts-sensorservice-sensor-sensorid-e.md) | 是 | 传感器类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Sensor | 使用同步方式返回传感器信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; <br> 2. Sensor service ipc exception;3. Sensor data channel exception. |
| [14500102](../errorcode-sensor.md#14500102-设备不支持该传感器) | The sensor is not supported by the device. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let ret = sensor.getSingleSensorSync(sensor.SensorId.ACCELEROMETER);
  console.info('Succeeded in getting sensor: ' + JSON.stringify(ret));
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get singleSensor . Code: ${e.code}, message: ${e.message}`);
}
```

