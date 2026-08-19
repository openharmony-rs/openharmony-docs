# getDeviceAltitude

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getDeviceAltitude

```TypeScript
function getDeviceAltitude(seaPressure: double, currentPressure: double, callback: AsyncCallback<double>): void
```

根据气压值获取海拔高度。使用callback异步回调。

**起始版本：** 23

<!--Device-sensor-function getDeviceAltitude(seaPressure: double, currentPressure: double, callback: AsyncCallback<double>): void--><!--Device-sensor-function getDeviceAltitude(seaPressure: double, currentPressure: double, callback: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| seaPressure | double | 是 | 海平面气压值，单位：hPa（百帕）。 |
| currentPressure | double | 是 | 指定的气压值，单位：hPa（百帕）。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;double&gt; | 是 | 回调函数，异步返回指定的气压值对应的海拔高度，单位：m（米）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; <br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let seaPressure = 1013.2;
  let currentPressure = 1500.0;
  sensor.getDeviceAltitude(seaPressure, currentPressure, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as number;
    if (error) {
      console.error(`Failed to get altitude. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeeded in getting altitude: ' + dataValue);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get altitude. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let seaPressure = 1013.2;
  let currentPressure = 1500.0;
  sensor.getDeviceAltitude(seaPressure, currentPressure, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as double;
    if (error) {
      console.error(`Failed to get altitude. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeeded in getting altitude: ' + dataValue);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get altitude. Code: ${e.code}, message: ${e.message}`);
}
```


## getDeviceAltitude

```TypeScript
function getDeviceAltitude(seaPressure: double, currentPressure: double): Promise<double>
```

根据气压值获取海拔高度。使用Promise异步回调。

**起始版本：** 23

<!--Device-sensor-function getDeviceAltitude(seaPressure: double, currentPressure: double): Promise<double>--><!--Device-sensor-function getDeviceAltitude(seaPressure: double, currentPressure: double): Promise<double>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| seaPressure | double | 是 | 海平面气压值，单位：hPa（百帕）。 |
| currentPressure | double | 是 | 指定的气压值，单位：hPa（百帕）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;double&gt; | Promise对象，使用异步方式返回指定的气压值对应的海拔高度，单位：m（米）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; <br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let seaPressure = 1013.2;
  let currentPressure = 1500.0;
  const promise = sensor.getDeviceAltitude(seaPressure, currentPressure);
  promise.then((data: number) => {
    console.info('Succeeded in getting sensor_getDeviceAltitude_Promise', data);
  }, (err: BusinessError) => {
    console.error(`Failed to get altitude. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get altitude. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let seaPressure = 1013.2;
  let currentPressure = 1500.0;
  const promise = sensor.getDeviceAltitude(seaPressure, currentPressure);
  promise.then((data: double) => {
    console.info('Succeeded in getting sensor_getDeviceAltitude_Promise', data);
  }, (err: BusinessError) => {
    console.error(`Failed to get altitude. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get altitude. Code: ${e.code}, message: ${e.message}`);
}
```

