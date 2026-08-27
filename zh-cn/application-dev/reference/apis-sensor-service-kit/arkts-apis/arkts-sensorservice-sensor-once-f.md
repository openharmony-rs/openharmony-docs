# once

## 导入模块

```TypeScript
```

## once

```TypeScript
function once(type: SensorId.ACCELEROMETER, callback: Callback<AccelerometerResponse>): void
```

获取一次加速度传感器数据。适用于无需持续监听、仅需一次性获取当前加速度数据的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ACCELEROMETER | 是 | 传感器类型，该值固定为SensorId.ACCELEROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;AccelerometerResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为AccelerometerResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.ACCELEROMETER, (data: sensor.AccelerometerResponse) => {
    console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback<AccelerometerUncalibratedResponse>): void
```

获取一次未校准加速度传感器数据。适用于仅需一次性获取原始加速度及偏移数据的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ACCELEROMETER_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.ACCELEROMETER_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为AccelerometerUncalibratedResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, (data: sensor.AccelerometerUncalibratedResponse) => {
    console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking once. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking once. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking once. Z-coordinate bias: ' + data.biasZ);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.AMBIENT_LIGHT, callback: Callback<LightResponse>): void
```

获取一次环境光传感器数据。适用于仅需一次性获取当前环境光强度的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.AMBIENT_LIGHT | 是 | 传感器类型，该值固定为SensorId.AMBIENT_LIGHT。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;LightResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为LightResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.AMBIENT_LIGHT, (data: sensor.LightResponse) => {
    console.info('Succeeded in invoking once. the ambient light intensity: ' + data.intensity);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback<AmbientTemperatureResponse>): void
```

获取一次温度传感器数据。适用于仅需一次性获取当前环境温度的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.AMBIENT_TEMPERATURE | 是 | 传感器类型，该值固定为SensorId.AMBIENT_TEMPERATURE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为AmbientTemperatureResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
    console.info('Succeeded in invoking once. Temperature: ' + data.temperature);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.BAROMETER, callback: Callback<BarometerResponse>): void
```

获取一次气压计传感器数据。适用于仅需一次性获取当前气压值的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.BAROMETER | 是 | 传感器类型，该值固定为SensorId.BAROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;BarometerResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为BarometerResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.BAROMETER, (data: sensor.BarometerResponse) => {
    console.info('Succeeded in invoking once. Atmospheric pressure: ' + data.pressure);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.GRAVITY, callback: Callback<GravityResponse>): void
```

获取一次重力传感器数据。适用于仅需一次性获取当前重力分量的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GRAVITY | 是 | 传感器类型，该值固定为SensorId.GRAVITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为GravityResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.GRAVITY, (data: sensor.GravityResponse) => {
    console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.GYROSCOPE, callback: Callback<GyroscopeResponse>): void
```

获取一次陀螺仪传感器数据。适用于仅需一次性获取当前旋转角速度的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**需要权限：** ohos.permission.GYROSCOPE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GYROSCOPE | 是 | 传感器类型，该值固定为SensorId.GYROSCOPE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GyroscopeResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为GyroscopeResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.GYROSCOPE, (data: sensor.GyroscopeResponse) => {
    console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback<GyroscopeUncalibratedResponse>): void
```

获取一次未校准陀螺仪传感器数据。适用于仅需一次性获取原始角速度及偏移数据的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**需要权限：** ohos.permission.GYROSCOPE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GYROSCOPE_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.GYROSCOPE_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为GyroscopeUncalibratedResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.GYROSCOPE_UNCALIBRATED, (data: sensor.GyroscopeUncalibratedResponse) => {
    console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking once. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking once. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking once. Z-coordinate bias: ' + data.biasZ);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.HALL, callback: Callback<HallResponse>): void
```

获取一次霍尔传感器数据。适用于仅需一次性检测当前霍尔状态的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HALL | 是 | 传感器类型，该值固定为SensorId.HALL。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为HallResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.HALL, (data: sensor.HallResponse) => {
    console.info('Succeeded in invoking once. Status: ' + data.status);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.HEART_RATE, callback: Callback<HeartRateResponse>): void
```

获取一次心率传感器数据。适用于仅需一次性获取当前心率值的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**需要权限：** ohos.permission.READ_HEALTH_DATA

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HEART_RATE | 是 | 传感器类型，该值固定为SensorId.HEART_RATE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;HeartRateResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为HeartRateResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.HEART_RATE, (data: sensor.HeartRateResponse) => {
    console.info('Succeeded in invoking once. Heart rate: ' + data.heartRate);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.HUMIDITY, callback: Callback<HumidityResponse>): void
```

获取一次湿度传感器数据。适用于仅需一次性获取当前环境湿度的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HUMIDITY | 是 | 传感器类型，该值固定为SensorId.HUMIDITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为HumidityResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.HUMIDITY, (data: sensor.HumidityResponse) => {
    console.info('Succeeded in invoking once. Humidity: ' + data.humidity);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback<LinearAccelerometerResponse>): void
```

获取一次线性加速度传感器数据。适用于仅需一次性获取当前线性加速度（不含重力分量）的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.LINEAR_ACCELEROMETER | 是 | 传感器类型，该值固定为SensorId.LINEAR_ACCELEROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为LinearAccelerometerResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.LINEAR_ACCELEROMETER, (data: sensor.LinearAccelerometerResponse) => {
    console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.MAGNETIC_FIELD, callback: Callback<MagneticFieldResponse>): void
```

获取一次磁场传感器数据。适用于仅需一次性获取当前磁场分量的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.MAGNETIC_FIELD | 是 | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为MagneticFieldResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.MAGNETIC_FIELD, (data: sensor.MagneticFieldResponse) => {
    console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback<MagneticFieldUncalibratedResponse>): void
```

获取一次未经校准的磁场传感器数据。适用于仅需一次性获取原始磁场及偏移数据的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.MAGNETIC_FIELD_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为MagneticFieldUncalibratedResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, (data: sensor.MagneticFieldUncalibratedResponse) => {
    console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking once. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking once. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking once. Z-coordinate bias: ' + data.biasZ);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.ORIENTATION, callback: Callback<OrientationResponse>): void
```

获取一次方向传感器数据。适用于仅需一次性获取当前设备方向的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ORIENTATION | 是 | 传感器类型，该值固定为SensorId.ORIENTATION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为OrientationResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.ORIENTATION, (data: sensor.OrientationResponse) => {
    console.info('Succeeded in the device rotating at an angle around the X axis: ' + data.beta);
    console.info('Succeeded in the device rotating at an angle around the Y axis: ' + data.gamma);
    console.info('Succeeded in the device rotating at an angle around the Z axis: ' + data.alpha);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.PEDOMETER, callback: Callback<PedometerResponse>): void
```

获取一次计步器传感器数据。计步传感器数据上报有一定延迟，延迟时间由具体的实现产品决定。适用于仅需一次性获取当前步数的场景。调用后，callback仅触发一次，自动取消订阅。

> **说明：**
> 
> 计步器传感器数据仅在设备重启时清零，不会每天清零，重启前上报的步数数据为累加值。

**起始版本：** 9

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PEDOMETER | 是 | Sensor type. 传感器类型，该值固定为SensorId.PEDOMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为PedometerResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.PEDOMETER, (data: sensor.PedometerResponse) => {
    console.info('Succeeded in invoking once. Step count: ' + data.steps);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.PEDOMETER_DETECTION, callback: Callback<PedometerDetectionResponse>): void
```

获取一次计步检测器传感器数据。适用于仅需一次性检测计步事件的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PEDOMETER_DETECTION | 是 | 传感器类型，该值固定为SensorId.PEDOMETER_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为PedometerDetectionResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
    console.info('Succeeded in invoking once. Scalar data: ' + data.scalar);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.PROXIMITY, callback: Callback<ProximityResponse>): void
```

获取一次接近光传感器数据。适用于仅需一次性检测当前接近状态的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PROXIMITY | 是 | 传感器类型，该值固定为SensorId.PROXIMITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ProximityResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为ProximityResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.PROXIMITY, (data: sensor.ProximityResponse) => {
    console.info('Succeeded in invoking once. Distance: ' + data.distance);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.ROTATION_VECTOR, callback: Callback<RotationVectorResponse>): void
```

获取一次旋转矢量传感器数据。适用于仅需一次性获取当前设备姿态的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ROTATION_VECTOR | 是 | 传感器类型，该值固定为SensorId.ROTATION_VECTOR。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为RotationVectorResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.ROTATION_VECTOR, (data: sensor.RotationVectorResponse) => {
    console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking once. Scalar quantity: ' + data.w);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.SIGNIFICANT_MOTION, callback: Callback<SignificantMotionResponse>): void
```

获取一次有效运动传感器数据。适用于仅需一次性检测有效运动的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.SIGNIFICANT_MOTION | 是 | 传感器类型，该值固定为SensorId.SIGNIFICANT_MOTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为SignificantMotionResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.SIGNIFICANT_MOTION, (data: sensor.SignificantMotionResponse) => {
    console.info('Succeeded in invoking once. Scalar data: ' + data.scalar);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorId.WEAR_DETECTION, callback: Callback<WearDetectionResponse>): void
```

获取一次佩戴检测传感器数据。适用于仅需一次性检测佩戴状态的场景。调用后，callback仅触发一次，自动取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.WEAR_DETECTION | 是 | 传感器类型，该值固定为SensorId.WEAR_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为WearDetectionResponse。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.once(sensor.SensorId.WEAR_DETECTION, (data: sensor.WearDetectionResponse) => {
    console.info('Succeeded in invoking once. Wear status: ' + data.value);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback<AccelerometerResponse>): void
```

监听加速度传感器的数据变化一次。适用于仅需一次性获取当前加速度数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ACCELEROMETER]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;)

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ACCELEROMETER | 是 | 加速度传感器类型为SENSOR_TYPE_ID_ACCELEROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;AccelerometerResponse&gt; | 是 | 注册一次加速度传感器的回调函数，上报的数据类型为AccelerometerResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER, (data: sensor.AccelerometerResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback: Callback<AccelerometerUncalibratedResponse>): void
```

监听未校准加速度传感器的数据变化一次。适用于仅需一次性获取当前未校准加速度数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ACCELEROMETER_UNCALIBRATED]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback&lt;AccelerometerUncalibratedResponse&gt;)

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED | 是 | 未校准加速度传感器类型为SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | 是 | 注册一次未校准加速度传感器的回调函数，上报的数据类型为AccelerometerUncalibratedResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, (data: sensor.AccelerometerUncalibratedResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking once. X-coordinate bias: ' + data.biasX);
  console.info('Succeeded in invoking once. Y-coordinate bias: ' + data.biasY);
  console.info('Succeeded in invoking once. Z-coordinate bias: ' + data.biasZ);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback<LightResponse>): void
```

监听环境光传感器数据变化一次。适用于仅需一次性获取当前环境光数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.AMBIENT_LIGHT]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT | 是 | 环境光传感器类型为SENSOR_TYPE_ID_AMBIENT_LIGHT。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;LightResponse&gt; | 是 | 注册一次环境光传感器的回调函数，上报的数据类型为LightResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, (data: sensor.LightResponse) => {
  console.info('Succeeded in invoking once. Illumination: ' + data.intensity);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback<AmbientTemperatureResponse>): void
```

监听环境温度传感器数据变化一次。适用于仅需一次性获取当前环境温度数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.AMBIENT_LIGHT]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback&lt;AmbientTemperatureResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE | 是 | 环境温度传感器类型为SENSOR_TYPE_ID_AMBIENT_TEMPERATURE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | 是 | 注册一次环境温度传感器的回调函数，上报的数据类型为AmbientTemperatureResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
  console.info('Succeeded in invoking once. Temperature: ' + data.temperature);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback<BarometerResponse>): void
```

监听气压计传感器数据变化一次。适用于仅需一次性获取当前气压数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.BAROMETER]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.BAROMETER, callback: Callback&lt;BarometerResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_BAROMETER | 是 | 气压计传感器类型为SENSOR_TYPE_ID_BAROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;BarometerResponse&gt; | 是 | 注册一次气压计传感器的回调函数，上报的数据类型为BarometerResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_BAROMETER, (data: sensor.BarometerResponse) => {
  console.info('Succeeded in invoking once. Atmospheric pressure: ' + data.pressure);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback<GravityResponse>): void
```

监听重力传感器的数据变化一次。适用于仅需一次性获取当前重力数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.GRAVITY]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.GRAVITY, callback: Callback&lt;GravityResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_GRAVITY | 是 | 重力传感器类型为SENSOR_TYPE_ID_GRAVITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | 是 | 注册一次重力传感器的回调函数，上报的数据类型为GravityResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_GRAVITY, (data: sensor.GravityResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  });
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback<GyroscopeResponse>): void
```

监听陀螺仪传感器的数据变化一次。适用于仅需一次性获取当前陀螺仪数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.GYROSCOPE]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;)

**需要权限：** ohos.permission.GYROSCOPE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_GYROSCOPE | 是 | 陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GyroscopeResponse&gt; | 是 | 注册一次陀螺仪传感器的回调函数，上报的数据类型为GyroscopeResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE, (data: sensor.GyroscopeResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback: Callback<GyroscopeUncalibratedResponse>): void
```

监听未校准陀螺仪传感器的数据变化一次。适用于仅需一次性获取当前未校准陀螺仪数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.GYROSCOPE_UNCALIBRATED]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback&lt;GyroscopeUncalibratedResponse&gt;)

**需要权限：** ohos.permission.GYROSCOPE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED | 是 | 未校准陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md)&gt; | 是 | 注册一次未校准陀螺仪传感器的回调函数， 上报的数据类型为GyroscopeUncalibratedResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, (data: sensor.GyroscopeUncalibratedResponse) => {
    console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking once. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking once. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking once. Z-coordinate bias: ' + data.biasZ);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback<HallResponse>): void
```

监听霍尔传感器数据变化一次。适用于仅需一次性获取当前霍尔数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.HALL]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.HALL, callback: Callback&lt;HallResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HALL | 是 | 霍尔传感器类型为SENSOR_TYPE_ID_HALL。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | 是 | 注册一次霍尔传感器的回调函数，上报的数据类型为HallResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_HALL, (data: sensor.HallResponse) => {
  console.info('Succeeded in invoking once. Status: ' + data.status);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback<HeartRateResponse>): void
```

监听心率传感器数据变化一次。适用于仅需一次性获取当前心率数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.HEART_RATE]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;)

**需要权限：** ohos.permission.HEART_RATE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HEART_RATE | 是 | 心率传感器类型为SENSOR_TYPE_ID_HEART_RATE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;HeartRateResponse&gt; | 是 | 注册一次心率传感器的回调函数，上报的数据类型为HeartRateResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_HEART_RATE, (data: sensor.HeartRateResponse) => {
  console.info("Succeeded in invoking once. Heart rate: " + data.heartRate);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback<HumidityResponse>): void
```

监听湿度传感器数据变化一次。适用于仅需一次性获取当前湿度数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.HUMIDITY]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.HUMIDITY, callback: Callback&lt;HumidityResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HUMIDITY | 是 | 湿度传感器类型为SENSOR_TYPE_ID_HUMIDITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md)&gt; | 是 | 注册一次湿度传感器的回调函数，上报的数据类型为HumidityResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_HUMIDITY, (data: sensor.HumidityResponse) => {
  console.info('Succeeded in invoking once. Humidity: ' + data.humidity);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback: Callback<LinearAccelerometerResponse>): void
```

监听线性加速度传感器数据变化一次。适用于仅需一次性获取当前线性加速度数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.LINEAR_ACCELEROMETER]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback&lt;LinearAccelerometerResponse&gt;)

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION | 是 | 线性加速度传感器类型为SENSOR_TYPE_ID_LINEAR_ACCELERATION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | 是 | 注册一次线性加速度传感器的回调函数， 上报的数据类型为LinearAccelerometerResponse。 |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback<MagneticFieldResponse>): void
```

监听磁场传感器数据变化一次。适用于仅需一次性获取当前磁场数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.MAGNETIC_FIELD]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD | 是 | 磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | 是 | 注册一次磁场传感器的回调函数，上报的数据类型为MagneticFieldResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, (data: sensor.MagneticFieldResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback<MagneticFieldUncalibratedResponse>): void
```

监听未校准磁场传感器数据变化一次。适用于仅需一次性获取当前未校准磁场数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.MAGNETIC_FIELD_UNCALIBRATED]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | 是 | 未校准磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | 是 | 注册一次未校准磁场传感器的回调函数， 上报的数据类型为MagneticFieldUncalibratedResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, (data: sensor.MagneticFieldUncalibratedResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking once. X-coordinate bias: ' + data.biasX);
  console.info('Succeeded in invoking once. Y-coordinate bias: ' + data.biasY);
  console.info('Succeeded in invoking once. Z-coordinate bias: ' + data.biasZ);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback<OrientationResponse>): void
```

监听方向传感器数据变化一次。适用于仅需一次性获取当前方向数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ORIENTATION]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.ORIENTATION, callback: Callback&lt;OrientationResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ORIENTATION | 是 | 方向传感器类型为SENSOR_TYPE_ID_ORIENTATION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | 是 | 注册一次方向传感器的回调函数，上报的数据类型为OrientationResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_ORIENTATION, (data: sensor.OrientationResponse) => {
  console.info('Succeeded in invoking the device rotating at an angle around the X axis: ' + data.beta);
  console.info('Succeeded in invoking the device rotating at an angle around the Y axis: ' + data.gamma);
  console.info('Succeeded in invoking the device rotating at an angle around the Z axis: ' + data.alpha);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback<PedometerResponse>): void
```

监听计步器传感器数据变化一次。适用于仅需一次性获取当前计步数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.PEDOMETER]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.PEDOMETER, callback: Callback&lt;PedometerResponse&gt;)

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_PEDOMETER | 是 | 计步传感器类型为SENSOR_TYPE_ID_PEDOMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | 是 | 注册一次计步传感器的回调函数，上报的数据类型为PedometerResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER, (data: sensor.PedometerResponse) => {
  console.info('Succeeded in invoking once. Steps: ' + data.steps);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback: Callback<PedometerDetectionResponse>): void
```

监听计步检测传感器数据变化一次。适用于仅需一次性获取当前计步检测数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.PEDOMETER_DETECTION]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.PEDOMETER_DETECTION, callback: Callback&lt;PedometerDetectionResponse&gt;)

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION | 是 | 计步检测传感器类型为SENSOR_TYPE_ID_PEDOMETER_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md)&gt; | 是 | 注册一次计步检测传感器的回调函数，上报的数据类型为PedometerDetectionResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
  console.info('Succeeded in invoking once. Scalar data: ' + data.scalar);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback<ProximityResponse>): void
```

监听接近光传感器数据变化一次。适用于仅需一次性获取当前接近光数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.PROXIMITY]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.PROXIMITY, callback: Callback&lt;ProximityResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_PROXIMITY | 是 | 接近光传感器类型为SENSOR_TYPE_ID_PROXIMITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ProximityResponse&gt; | 是 | 注册一次接近光传感器的回调函数，上报的数据类型为ProximityResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_PROXIMITY, (data: sensor.ProximityResponse) => {
  console.info('Succeeded in invoking once. Distance: ' + data.distance);
}
);
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback<RotationVectorResponse>): void
```

监听旋转矢量传感器数据变化一次。适用于仅需一次性获取当前旋转矢量数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ROTATION_VECTOR]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR | 是 | 旋转矢量传感器类型为SENSOR_TYPE_ID_ROTATION_VECTOR。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | 是 | 注册一次旋转矢量传感器的回调函数，上报的数据类型为RotationVectorResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, (data: sensor.RotationVectorResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking once. Scalar quantity: ' + data.w);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback<SignificantMotionResponse>): void
```

监听有效运动传感器的数据变化一次。适用于仅需一次性获取当前有效运动数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.SIGNIFICANT_MOTION]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION | 是 | 有效运动传感器类型为SENSOR_TYPE_ID_SIGNIFICANT_MOTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | 是 | 注册一次有效运动传感器的回调函数，上报的数据类型为SignificantMotionResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, (data: sensor.SignificantMotionResponse) => {
  console.info('Succeeded in invoking once. Scalar data: ' + data.scalar);
});
```


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback<WearDetectionResponse>): void
```

监听所佩戴的检测传感器的数据变化一次。适用于仅需一次性获取当前佩戴检测数据的场景。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.WEAR_DETECTION]
> once
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [once](#once)(type: SensorId.WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_WEAR_DETECTION | 是 | 佩戴检测传感器类型为SENSOR_TYPE_ID_WEAR_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | 是 | 注册一次穿戴检测传感器的回调函数，上报的数据类型为WearDetectionResponse。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, (data: sensor.WearDetectionResponse) => {
  console.info("Succeeded in invoking once. Wear status: " + data.value);
});
```
