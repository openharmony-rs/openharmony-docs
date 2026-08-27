# on

## 导入模块

```TypeScript
```

## on

```TypeScript
function on(type: SensorId.ACCELEROMETER, callback: Callback<AccelerometerResponse>,
    options?: Options): void
```

订阅加速度传感器数据。加速度传感器用于测量设备在X、Y、Z三个方向上的加速度，包含重力加速度分量。适用于需要感知设备运动状态、实现屏幕旋转、游戏操控、计步等场景。 调用后，系统会按设定频率通过callback持续上报加速度数据。

**起始版本：** 9

**需要权限：** ohos.permission.ACCELEROMETER

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ACCELEROMETER | 是 | 传感器类型，该值固定为SensorId.ACCELEROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;AccelerometerResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为AccelerometerResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅加速度传感器数据
  sensor.on(sensor.SensorId.ACCELEROMETER, (data: sensor.AccelerometerResponse) => {
    // 输出X、Y、Z坐标分量
    console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.ACCELEROMETER);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback<AccelerometerUncalibratedResponse>,
    options?: Options): void
```

订阅未校准加速度传感器数据。未校准加速度传感器与加速度传感器的区别在于，其上报的偏移值(biasX/biasY/biasZ)未经系统校准补偿，适用于需要获取原始加速度数据或自行实现校准算法的场景。 与sensor.on('SensorId.ACCELEROMETER')相比，本接口额外提供偏移值信息，适用于需要分析设备校准偏差的场景。

**起始版本：** 9

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ACCELEROMETER_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.ACCELEROMETER_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为AccelerometerUncalibratedResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅未校准加速度传感器数据
  sensor.on(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, (data: sensor.AccelerometerUncalibratedResponse) => {
    // 输出X、Y、Z坐标分量和偏移值
    console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking on. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking on. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking on. Z-coordinate bias: ' + data.biasZ);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.ACCELEROMETER_UNCALIBRATED);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.AMBIENT_LIGHT, callback: Callback<LightResponse>, options?: Options): void
```

订阅环境光传感器数据。环境光传感器用于测量周围环境的光照强度，适用于自动调节屏幕亮度、判断环境明暗等场景。调用后，系统会按设定频率通过callback持续上报环境光强度数据。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.AMBIENT_LIGHT | 是 | 传感器类型，该值固定为SensorId.AMBIENT_LIGHT。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;LightResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为LightResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅环境光传感器数据
  sensor.on(sensor.SensorId.AMBIENT_LIGHT, (data: sensor.LightResponse) => {
    // 输出环境光强度
    console.info('Succeeded in getting the ambient light intensity: ' + data.intensity);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.AMBIENT_LIGHT);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback<AmbientTemperatureResponse>,
    options?: Options): void
```

订阅环境温度传感器数据。温度传感器用于测量设备周围的环境温度，适用于环境温度监测、温度补偿等场景。调用后，系统会按设定频率通过callback持续上报温度数据。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.AMBIENT_TEMPERATURE | 是 | 传感器类型，该值固定为SensorId.AMBIENT_TEMPERATURE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为AmbientTemperatureResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅温度传感器数据
  sensor.on(sensor.SensorId.AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
    // 输出温度值
    console.info('Succeeded in invoking on. Temperature: ' + data.temperature);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.AMBIENT_TEMPERATURE);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.BAROMETER, callback: Callback<BarometerResponse>, options?: Options): void
```

订阅气压计传感器数据。气压计传感器用于测量大气压强，适用于海拔估算、天气预报辅助等场景。调用后，系统会按设定频率通过callback持续上报气压数据。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.BAROMETER | 是 | 传感器类型，该值固定为SensorId.BAROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;BarometerResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为BarometerResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅气压计传感器数据
  sensor.on(sensor.SensorId.BAROMETER, (data: sensor.BarometerResponse) => {
    // 输出气压值
    console.info('Succeeded in invoking on. Atmospheric pressure: ' + data.pressure);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.BAROMETER);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.GRAVITY, callback: Callback<GravityResponse>,
    options?: Options): void
```

订阅重力传感器数据。重力传感器用于测量设备在X、Y、Z三个方向上受到的重力加速度分量，适用于需要分离重力分量进行运动分析的场景，如游戏操控、运动检测。 调用后，系统会按设定频率通过callback持续上报重力分量数据。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GRAVITY | 是 | 传感器类型，该值固定为SensorId.GRAVITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为GravityResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅重力传感器数据
  sensor.on(sensor.SensorId.GRAVITY, (data: sensor.GravityResponse) => {
    // 输出X、Y、Z坐标分量
    console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.GRAVITY);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.GYROSCOPE, callback: Callback<GyroscopeResponse>,
    options?: Options): void
```

订阅校准的陀螺仪传感器数据。陀螺仪传感器用于测量设备绕X、Y、Z轴的旋转角速度，适用于设备旋转检测、姿态跟踪、游戏操控等场景。调用后，系统会按设定频率通过callback持续上报角速度数据。

**起始版本：** 9

**需要权限：** ohos.permission.GYROSCOPE

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GYROSCOPE | 是 | 传感器类型，该值固定为SensorId.GYROSCOPE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GyroscopeResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为GyroscopeResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅校准的陀螺仪传感器数据
  sensor.on(sensor.SensorId.GYROSCOPE, (data: sensor.GyroscopeResponse) => {
    // 输出X、Y、Z坐标分量
    console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.GYROSCOPE);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback<GyroscopeUncalibratedResponse>,
    options?: Options): void
```

订阅未校准陀螺仪传感器数据。未校准陀螺仪传感器与陀螺仪传感器的区别在于，其上报的偏移值(biasX/biasY/biasZ)未经系统校准补偿，适用于需要获取原始陀螺仪数据或自行实现校准算法的场景。 与sensor.on('SensorId.GYROSCOPE')相比，本接口额外提供偏移值信息，适用于需要分析设备陀螺仪校准偏差的场景。

**起始版本：** 9

**需要权限：** ohos.permission.GYROSCOPE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GYROSCOPE_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.GYROSCOPE_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为GyroscopeUncalibratedResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅未校准陀螺仪传感器数据
  sensor.on(sensor.SensorId.GYROSCOPE_UNCALIBRATED, (data: sensor.GyroscopeUncalibratedResponse) => {
    // 输出X、Y、Z坐标分量和偏移值
    console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking on. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking on. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking on. Z-coordinate bias: ' + data.biasZ);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.GYROSCOPE_UNCALIBRATED);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.HALL, callback: Callback<HallResponse>, options?: Options): void
```

订阅霍尔传感器数据。霍尔传感器用于检测磁场变化，常用于检测翻盖手机或皮套的开合状态。当霍尔事件被触发得较为频繁时，可通过options参数限定事件上报频率。 调用后，系统会通过callback持续上报霍尔状态数据。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HALL | 是 | 传感器类型，该值固定为SensorId.HALL。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为HallResponse。 |
| options | Options | 否 | 可选参数列表，当霍尔事件被触发的很频繁时，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅霍尔传感器数据
  sensor.on(sensor.SensorId.HALL, (data: sensor.HallResponse) => {
    // 输出霍尔状态
    console.info('Succeeded in invoking on. Hall status: ' + data.status);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.HALL);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.HEART_RATE, callback: Callback<HeartRateResponse>,
    options?: Options): void
```

订阅心率传感器数据。心率传感器用于测量用户的心率值，适用于健康监测、运动辅助等场景。调用后，系统会按设定频率通过callback持续上报心率数据。

**起始版本：** 9

**需要权限：** ohos.permission.READ_HEALTH_DATA

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HEART_RATE | 是 | 传感器类型，该值固定为SensorId.HEART_RATE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;HeartRateResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为HeartRateResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅心率传感器数据
  sensor.on(sensor.SensorId.HEART_RATE, (data: sensor.HeartRateResponse) => {
    // 输出心率值
    console.info('Succeeded in invoking on. Heart rate: ' + data.heartRate);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.HEART_RATE);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.HUMIDITY, callback: Callback<HumidityResponse>,
    options?: Options): void
```

订阅湿度传感器数据。湿度传感器用于测量周围环境的相对湿度，适用于环境湿度监测、智能家居联动等场景。调用后，系统会按设定频率通过callback持续上报湿度数据。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HUMIDITY | 是 | 传感器类型，该值固定为SensorId.HUMIDITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为HumidityResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅湿度传感器数据
  sensor.on(sensor.SensorId.HUMIDITY, (data: sensor.HumidityResponse) => {
    // 输出湿度值
    console.info('Succeeded in invoking on. Humidity: ' + data.humidity);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.HUMIDITY);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback<LinearAccelerometerResponse>,
    options?: Options): void
```

订阅线性加速度传感器数据。线性加速度传感器用于测量设备在X、Y、Z三个方向上的加速度（不含重力加速度分量），适用于需要感知设备纯粹运动加速度的场景，如运动追踪、碰撞检测。 与sensor.on('SensorId.ACCELEROMETER')相比，本接口已去除重力分量，适用于仅需设备运动加速度的场景。

**起始版本：** 9

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.LINEAR_ACCELEROMETER | 是 | 传感器类型，该值固定为SensorId.LINEAR_ACCELEROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为LinearAccelerometerResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅线性加速度传感器数据
  sensor.on(sensor.SensorId.LINEAR_ACCELEROMETER, (data: sensor.LinearAccelerometerResponse) => {
    // 输出X、Y、Z坐标分量
    console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.LINEAR_ACCELEROMETER);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.MAGNETIC_FIELD, callback: Callback<MagneticFieldResponse>,
    options?: Options): void
```

订阅地磁传感器数据。地磁传感器用于测量设备周围的磁场强度在X、Y、Z三个方向上的分量，适用于指南针、方向检测、金属检测等场景。调用后，系统会按设定频率通过callback持续上报磁场分量数据。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.MAGNETIC_FIELD | 是 | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为MagneticFieldResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅地磁传感器数据
  sensor.on(sensor.SensorId.MAGNETIC_FIELD, (data: sensor.MagneticFieldResponse) => {
    // 输出X、Y、Z坐标分量
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


## on

```TypeScript
function on(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback<MagneticFieldUncalibratedResponse>,
    options?: Options): void
```

订阅未校准地磁传感器数据。未校准地磁传感器与地磁传感器的区别在于，其上报的偏移值(biasX/biasY/biasZ)未经系统校准补偿，适用于需要获取原始磁场数据或自行实现校准算法的场景。 与sensor.on('SensorId.MAGNETIC_FIELD')相比，本接口额外提供偏移值信息，适用于需要分析设备地磁校准偏差的场景。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.MAGNETIC_FIELD_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为MagneticFieldUncalibratedResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅未校准地磁传感器数据
  sensor.on(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, (data: sensor.MagneticFieldUncalibratedResponse) => {
    // 输出X、Y、Z坐标分量和偏移值
    console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking on. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking on. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking on. Z-coordinate bias: ' + data.biasZ);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.ORIENTATION, callback: Callback<OrientationResponse>,
    options?: Options): void
```

订阅方向传感器数据。方向传感器用于测量设备绕Z轴旋转的角度(alpha)、绕X轴旋转的角度(beta)和绕Y轴旋转的角度(gamma)，适用于屏幕旋转、指南针、姿态感知等场景。 调用后，系统会按设定频率通过callback持续上报方向数据。调用本接口的应用或服务可以通过提示用户使用8字校准法来提高应用获取的方向传感器的精度，此传感器理论误差正负5度，具体的精度根据不同的驱动及算法实现可能存在差异。

> **说明：**
> 
> 调用本接口的应用或服务可以通过提示用户使用8字校准法来提高应用获取的方向传感器的精度，此传感器理论误差正负5度，具体的精度根据不同的驱动及算法实现可能存在差异。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ORIENTATION | 是 | 传感器类型，该值固定为SensorId.ORIENTATION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为OrientationResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅方向传感器数据
  sensor.on(sensor.SensorId.ORIENTATION, (data: sensor.OrientationResponse) => {
    // 输出设备绕Z、X、Y轴旋转的角度
    console.info('Succeeded in the device rotating at an angle around the Z axis: ' + data.alpha);
    console.info('Succeeded in the device rotating at an angle around the X axis: ' + data.beta);
    console.info('Succeeded in the device rotating at an angle around the Y axis: ' + data.gamma);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.ORIENTATION);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.PEDOMETER, callback: Callback<PedometerResponse>, options?: Options): void
```

订阅计步器传感器数据。计步器传感器用于统计用户的步行步数，适用于运动追踪、健康管理等场景。计步传感器数据上报有一定延迟，延迟时间由具体的实现产品决定。调用后，系统会按设定频率通过callback持续上报步数数据。

> **说明：**
> 
> 计步器传感器数据仅在设备重启时清零，不会每天清零，重启前上报的步数数据为累加值。

**起始版本：** 9

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PEDOMETER | 是 | 传感器类型，该值固定为SensorId.PEDOMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为PedometerResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅计步器传感器数据
  sensor.on(sensor.SensorId.PEDOMETER, (data: sensor.PedometerResponse) => {
    // 输出步数
    console.info('Succeeded in invoking on. Step count: ' + data.steps);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.PEDOMETER);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.PEDOMETER_DETECTION, callback: Callback<PedometerDetectionResponse>,
    options?: Options): void
```

订阅计步检测器传感器数据。计步检测器传感器用于检测用户是否发生了计步事件（如迈步动作），适用于需要实时检测步行状态的场景。与sensor.on('SensorId.PEDOMETER')相比，本接口上报的是计步事件标量而非累计步数， 适用于需要检测单步事件的场景。

**起始版本：** 9

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PEDOMETER_DETECTION | 是 | 传感器类型，该值固定为SensorId.PEDOMETER_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为PedometerDetectionResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅计步检测器传感器数据
  sensor.on(sensor.SensorId.PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
    // 输出计步标量值
    console.info('Succeeded in invoking on. Pedometer scalar: ' + data.scalar);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.PEDOMETER_DETECTION);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.PROXIMITY, callback: Callback<ProximityResponse>, options?: Options): void
```

订阅接近光传感器数据。接近光传感器用于检测物体与设备的距离状态，常用于通话时自动关闭屏幕以防止误触。当接近光事件被触发得较为频繁时，可通过options参数限定事件上报频率。 调用后，系统会通过callback持续上报接近状态数据。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PROXIMITY | 是 | 传感器类型，该值固定为SensorId.PROXIMITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ProximityResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为ProximityResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。当接近光事件被触发的很频繁时，该参数用于限定事件上报的频率。 |

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
  // 订阅接近光传感器数据
  sensor.on(sensor.SensorId.PROXIMITY, (data: sensor.ProximityResponse) => {
    // 输出距离值
    console.info('Succeeded in invoking on. Distance: ' + data.distance);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.PROXIMITY);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.ROTATION_VECTOR, callback: Callback<RotationVectorResponse>,
    options?: Options): void
```

订阅旋转矢量传感器数据。旋转矢量传感器用于表示设备的姿态旋转，数据由X、Y、Z分量和标量W组成，可用于设备姿态估计、AR/VR场景等。调用后，系统会按设定频率通过callback持续上报旋转矢量数据。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ROTATION_VECTOR | 是 | 传感器类型，该值固定为SensorId.ROTATION_VECTOR。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为RotationVectorResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  sensor.on(sensor.SensorId.ROTATION_VECTOR, (data: sensor.RotationVectorResponse) => {
    console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking on. Scalar quantity: ' + data.w);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.ROTATION_VECTOR);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.SIGNIFICANT_MOTION, callback: Callback<SignificantMotionResponse>,
    options?: Options): void
```

订阅有效运动传感器数据，用于检测用户拿起设备、明显移动或剧烈摇晃等有效运动事件。适用于需要根据用户活动状态唤醒设备、启动应用或切换模式的场景。调用后，系统会通过callback持续上报有效运动事件数据。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.SIGNIFICANT_MOTION | 是 | 传感器类型，该值固定为SensorId.SIGNIFICANT_MOTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为SignificantMotionResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  sensor.on(sensor.SensorId.SIGNIFICANT_MOTION, (data: sensor.SignificantMotionResponse) => {
    console.info('Succeeded in invoking on. Scalar data: ' + data.scalar);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.SIGNIFICANT_MOTION);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.WEAR_DETECTION, callback: Callback<WearDetectionResponse>,
    options?: Options): void
```

订阅佩戴检测传感器数据。佩戴检测传感器用于检测设备是否被用户佩戴，适用于智能手表等可穿戴设备的佩戴状态检测，以便自动切换工作模式。调用后，系统会按设定频率通过callback持续上报佩戴状态数据。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.WEAR_DETECTION | 是 | 传感器类型，该值固定为SensorId.WEAR_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为WearDetectionResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  sensor.on(sensor.SensorId.WEAR_DETECTION, (data: sensor.WearDetectionResponse) => {
    console.info('Succeeded in invoking on. Wear status: ' + data.value);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.WEAR_DETECTION);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorId.FUSION_PRESSURE, callback: Callback<FusionPressureResponse>,
    options?: Options): void
```

订阅融合压力传感器数据。融合压力传感器用于获取经融合算法处理的压力数据，仅适用于智能手表设备。适用于需要获取手腕压力数据的健康监测场景。调用后，系统会按设定频率通过callback持续上报融合压力数据。

**起始版本：** 22

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.FUSION_PRESSURE | 是 | 传感器类型，该值固定为SensorId.FUSION_PRESSURE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FusionPressureResponse](arkts-sensorservice-sensor-fusionpressureresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为FusionPressureResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

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
  // 订阅融合压力传感器数据
  sensor.on(sensor.SensorId.FUSION_PRESSURE, (data: sensor.FusionPressureResponse) => {
    // 输出融合压力值
    console.info('Succeeded in invoking on. fusionPressure: ' + data.fusionPressure);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.FUSION_PRESSURE);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback<AccelerometerResponse>,
    options?: Options): void
```

监听加速度传感器的数据变化。适用于需要感知设备运动状态、实现屏幕旋转或游戏操控的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ACCELEROMETER]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;, options?: Options)

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ACCELEROMETER | 是 | 要订阅的加速度传感器类型为SENSOR_TYPE_ID_ACCELEROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;AccelerometerResponse&gt; | 是 | 注册加速度传感器的回调函数，上报的数据类型为AccelerometerResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER, (data: sensor.AccelerometerResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback: Callback<AccelerometerUncalibratedResponse>,
    options?: Options): void
```

监听未校准加速度传感器的数据变化。适用于需要获取包含偏差校准数据的加速度原始数据的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ACCELEROMETER_UNCALIBRATED]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback&lt;AccelerometerUncalibratedResponse&gt;, options?: Options)

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED | 是 | 要订阅的未校准加速度传感器类型为SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | 是 | 注册未校准加速度传感器的回调函数，上报的数据类型为AccelerometerUncalibratedResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, (data: sensor.AccelerometerUncalibratedResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking on. X-coordinate bias: ' + data.biasX);
  console.info('Succeeded in invoking on. Y-coordinate bias: ' + data.biasY);
  console.info('Succeeded in invoking on. Z-coordinate bias: ' + data.biasZ);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback<LightResponse>,
    options?: Options): void
```

监听环境光传感器的数据变化。适用于需要感知环境光照强度的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.AMBIENT_LIGHT]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT | 是 | 要订阅的环境光传感器类型为SENSOR_TYPE_ID_AMBIENT_LIGHT。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;LightResponse&gt; | 是 | 注册环境光传感器的回调函数，上报的数据类型为LightResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, (data: sensor.LightResponse) => {
  console.info('Succeeded in invoking on. Illumination: ' + data.intensity);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback<AmbientTemperatureResponse>,
    options?: Options): void
```

监听环境温度传感器的数据变化。适用于需要感知环境温度的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.AMBIENT_TEMPERATURE]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback&lt;AmbientTemperatureResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE | 是 | 要订阅的环境温度传感器类型为SENSOR_TYPE_ID_AMBIENT_TEMPERATURE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | 是 | 注册环境温度传感器的回调函数，上报的数据类型为AmbientTemperatureResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
  console.info('Succeeded in invoking on. Temperature: ' + data.temperature);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback<BarometerResponse>,
    options?: Options): void
```

监听气压计传感器的数据变化。适用于需要感知环境气压的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.BAROMETER]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.BAROMETER, callback: Callback&lt;BarometerResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_BAROMETER | 是 | 要订阅的气压计传感器类型为SENSOR_TYPE_ID_BAROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;BarometerResponse&gt; | 是 | 注册气压计传感器的回调函数，上报的数据类型为BarometerResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_BAROMETER, (data: sensor.BarometerResponse) => {
  console.info('Succeeded in invoking on. Atmospheric pressure: ' + data.pressure);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback<GravityResponse>,
    options?: Options): void
```

监听重力传感器的数据变化。适用于需要感知设备重力方向的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.GRAVITY]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.GRAVITY, callback: Callback&lt;GravityResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_GRAVITY | 是 | 要订阅的重力传感器类型为SENSOR_TYPE_ID_GRAVITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | 是 | 注册重力传感器的回调函数，上报的数据类型为GravityResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_GRAVITY, (data: sensor.GravityResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback<GyroscopeResponse>,
    options?: Options): void
```

监听陀螺仪传感器的数据变化。适用于需要感知设备旋转角速度的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.GYROSCOPE]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;, options?: Options)

**需要权限：** ohos.permission.GYROSCOPE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_GYROSCOPE | 是 | 要订阅的陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GyroscopeResponse&gt; | 是 | 注册陀螺仪传感器的回调函数，上报的数据类型为GyroscopeResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE, (data: sensor.GyroscopeResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback: Callback<GyroscopeUncalibratedResponse>,
    options?: Options): void
```

监听未校准陀螺仪传感器的数据变化。适用于需要获取包含偏差校准数据的陀螺仪原始数据的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.GYROSCOPE_UNCALIBRATED]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback&lt;GyroscopeUncalibratedResponse&gt;, options?: Options)

**需要权限：** ohos.permission.GYROSCOPE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED | 是 | 要订阅的未校准陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md)&gt; | 是 | 注册未校准陀螺仪传感器的回调函数，上报的数据类型为GyroscopeUncalibratedResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, (data: sensor.GyroscopeUncalibratedResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking on. X-coordinate bias: ' + data.biasX);
  console.info('Succeeded in invoking on. Y-coordinate bias: ' + data.biasY);
  console.info('Succeeded in invoking on. Z-coordinate bias: ' + data.biasZ);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback<HallResponse>,
    options?: Options): void
```

监听霍尔传感器的数据变化。适用于需要检测设备翻盖或磁铁状态的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.HALL]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.HALL, callback: Callback&lt;HallResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HALL | 是 | 要订阅的霍尔传感器类型为SENSOR_TYPE_ID_HALL。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | 是 | 注册霍尔传感器的回调函数，上报的数据类型为 HallResponse。 |
| options | Options | 否 | 可选参数列表，当霍尔事件被触发的很频繁时，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_HALL, (data: sensor.HallResponse) => {
  console.info('Succeeded in invoking on. Status: ' + data.status);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback<HeartRateResponse>,
    options?: Options): void
```

监听心率传感器的数据变化。适用于需要获取用户心率数据的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.HEART_RATE]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;, options?: Options)

**需要权限：** ohos.permission.HEALTH_DATA

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HEART_RATE | 是 | 要订阅的心率传感器类型为SENSOR_TYPE_ID_HEART_RATE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;HeartRateResponse&gt; | 是 | 注册心率传感器的回调函数，上报的数据类型为HeartRateResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback<HumidityResponse>,
    options?: Options): void
```

监听湿度传感器的数据变化。适用于需要感知环境湿度的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.HUMIDITY]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.HUMIDITY, callback: Callback&lt;HumidityResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HUMIDITY | 是 | 要订阅的湿度传感器类型为SENSOR_TYPE_ID_HUMIDITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md)&gt; | 是 | 注册湿度传感器的回调函数，上报的数据类型为HumidityResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_HUMIDITY, (data: sensor.HumidityResponse) => {
  console.info('Succeeded in invoking on. Humidity: ' + data.humidity);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback: Callback<LinearAccelerometerResponse>,
    options?: Options): void
```

监听线性加速度传感器的数据变化。适用于需要获取排除重力影响的线性加速度数据的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.LINEAR_ACCELEROMETER]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback&lt;LinearAccelerometerResponse&gt;, options?: Options)

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION | 是 | 要订阅的线性加速度传感器类型为SENSOR_TYPE_ID_LINEAR_ACCELERATION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | 是 | 注册线性加速度传感器的回调函数，上报的数据类型为LinearAccelerometerResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback<MagneticFieldResponse>,
    options?: Options): void
```

监听磁场传感器的数据变化。适用于需要感知设备周围磁场强度与方向的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.MAGNETIC_FIELD]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD | 是 | 要订阅的磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | 是 | 注册磁场传感器的回调函数，上报的数据类型为MagneticFieldResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, (data: sensor.MagneticFieldResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback<MagneticFieldUncalibratedResponse>,
    options?: Options): void
```

监听未校准磁场传感器的数据变化。适用于需要获取包含偏差校准数据的磁场原始数据的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.MAGNETIC_FIELD_UNCALIBRATED]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | 是 | 要订阅的未校准磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | 是 | 注册未校准磁场传感器的回调函数，上报的数据类型为MagneticFieldUncalibratedResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, (data: sensor.MagneticFieldUncalibratedResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking on. X-coordinate bias: ' + data.biasX);
  console.info('Succeeded in invoking on. Y-coordinate bias: ' + data.biasY);
  console.info('Succeeded in invoking on. Z-coordinate bias: ' + data.biasZ);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback<OrientationResponse>,
    options?: Options): void
```

监听方向传感器的数据变化。适用于需要感知设备姿态方向的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ORIENTATION]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.ORIENTATION, callback: Callback&lt;OrientationResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ORIENTATION | 是 | 要订阅的方向传感器类型为SENSOR_TYPE_ID_ORIENTATION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | 是 | 注册方向传感器的回调函数，上报的数据类型为OrientationResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_ORIENTATION, (data: sensor.OrientationResponse) => {
  console.info('Succeeded in the device rotating at an angle around the X axis: ' + data.beta);
  console.info('Succeeded in the device rotating at an angle around the Y axis: ' + data.gamma);
  console.info('Succeeded in the device rotating at an angle around the Z axis: ' + data.alpha);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback<PedometerResponse>,
    options?: Options): void
```

监听计步传感器的数据变化。适用于需要获取用户步数数据的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.PEDOMETER]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.PEDOMETER, callback: Callback&lt;PedometerResponse&gt;, options?: Options)

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_PEDOMETER | 是 | 要订阅的计步传感器类型为SENSOR_TYPE_ID_PEDOMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | 是 | 注册计步传感器的回调函数，上报的数据类型为PedometerResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER, (data: sensor.PedometerResponse) => {
  console.info('Succeeded in invoking on. Steps: ' + data.steps);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback: Callback<PedometerDetectionResponse>,
    options?: Options): void
```

监听计步检测传感器的数据变化。适用于需要检测用户是否在行走的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.PEDOMETER_DETECTION]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.PEDOMETER_DETECTION, callback: Callback&lt;PedometerDetectionResponse&gt;, options?: Options)

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION | 是 | 要订阅的计步检测传感器类型为SENSOR_TYPE_ID_PEDOMETER_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md)&gt; | 是 | 注册计步检测传感器的回调函数，上报的数据类型为PedometerDetectionResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
  console.info('Succeeded in invoking on. Scalar data: ' + data.scalar);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback<ProximityResponse>,
    options?: Options): void
```

监听接近光传感器的数据变化。适用于需要感知设备前方是否有物体靠近的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.PROXIMITY]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.PROXIMITY, callback: Callback&lt;ProximityResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_PROXIMITY | 是 | 要订阅的接近光传感器类型为SENSOR_TYPE_ID_PROXIMITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ProximityResponse&gt; | 是 | 注册接近光传感器的回调函数，上报的数据类型为ProximityResponse。 |
| options | Options | 否 | 可选参数列表，当接近光事件被触发的很频繁时，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PROXIMITY, (data: sensor.ProximityResponse) => {
  console.info('Succeeded in invoking on. Distance: ' + data.distance);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback<RotationVectorResponse>,
    options?: Options): void
```

监听旋转矢量传感器的数据变化。适用于需要感知设备三维空间旋转状态的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ROTATION_VECTOR]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR | 是 | 要订阅的旋转矢量传感器类型为SENSOR_TYPE_ID_ROTATION_VECTOR。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | 是 | 注册旋转矢量传感器的回调函数，上报的数据类型为RotationVectorResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, (data: sensor.RotationVectorResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking on. Scalar quantity: ' + data.w);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback<SignificantMotionResponse>,
    options?: Options): void
```

监听有效运动传感器数据变化。适用于需要检测设备是否有显著运动的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.SIGNIFICANT_MOTION]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION | 是 | 要订阅的有效运动传感器类型为SENSOR_TYPE_ID_SIGNIFICANT_MOTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | 是 | 注册有效运动传感器的回调函数，上报的数据类型为SignificantMotionResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, (data: sensor.SignificantMotionResponse) => {
  console.info('Succeeded in invoking on. Scalar data: ' + data.scalar);
},
  { interval: 100000000 }
);
```


## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback<WearDetectionResponse>,
    options?: Options): void
```

监听所佩戴的检测传感器的数据变化。适用于需要检测设备是否被佩戴的场景。如果多次调用该接口，仅最后一次调用生效。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.WEAR_DETECTION]
> on
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](#on)(type: SensorId.WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;, options?: Options)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_WEAR_DETECTION | 是 | 要订阅的佩戴检测传感器类型为SENSOR_TYPE_ID_WEAR_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | 是 | 注册佩戴检测传感器的回调函数，上报的数据类型为WearDetectionResponse。 |
| options | Options | 否 | 用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, (data: sensor.WearDetectionResponse) => {
  console.info('Succeeded in invoking on. Wear status: ' + data.value);
},
  { interval: 100000000 }
);
```


## on('sensorStatusChange')

```TypeScript
function on(type: 'sensorStatusChange', callback: Callback<SensorStatusEvent>): void
```

监听传感器上线下线状态的变化，callback返回传感器状态事件数据。适用于需要感知传感器设备动态上下线的场景，如远程传感器连接或断开时自动更新传感器列表或订阅状态。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sensorStatusChange' | 是 | 固定传入'sensorStatusChange'，状态监听固定参数。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SensorStatusEvent](arkts-sensorservice-sensor-sensorstatusevent-i.md)&gt; | 是 | 回调函数，异步上报的传感器事件数据SensorStatusEvent。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on('sensorStatusChange', (data: sensor.SensorStatusEvent) => {
    console.info('sensorStatusChange : ' + JSON.stringify(data));
  });
  setTimeout(() => {
    sensor.off('sensorStatusChange');
  }, 5000);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```
