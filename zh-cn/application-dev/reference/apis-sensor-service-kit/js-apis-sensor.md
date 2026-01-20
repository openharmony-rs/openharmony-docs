# @ohos.sensor (传感器)

sensor模块提供了获取传感器数据的能力，包括获取传感器属性列表，订阅传感器数据，以及一些通用的传感器算法。

> **说明：**
> 
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。订阅前可使用[getSingleSensor](#sensorgetsinglesensor9)接口获取该传感器的信息，订阅传感器数据时确保on订阅和off取消订阅成对出现。


## 导入模块

```ts
import { sensor } from '@kit.SensorServiceKit';
```

## sensor.on(ACCELEROMETER)<sup>9+</sup>

on(type: SensorId.ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;, options?: Options): void

订阅加速度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onAccelerometerChange](#sensoronaccelerometerchange23)

**需要权限**：ohos.permission.ACCELEROMETER

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).ACCELEROMETER                         | 是   | 传感器类型，该值固定为SensorId.ACCELEROMETER。              |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AccelerometerResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.ACCELEROMETER, (data: sensor.AccelerometerResponse) => {
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

## sensor.onAccelerometerChange<sup>23+</sup>

onAccelerometerChange(callback: Callback&lt;AccelerometerResponse&gt;, options?: Options): void

订阅加速度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(ACCELEROMETER)](#sensoronaccelerometer9)

**需要权限**：ohos.permission.ACCELEROMETER

**原子化服务API**：从API Version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AccelerometerResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onAccelerometerChange((data: sensor.AccelerometerResponse) => {
    console.info('Succeeded in invoking onAccelerometerChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onAccelerometerChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onAccelerometerChange. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offAccelerometerChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onAccelerometerChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(ACCELEROMETER_UNCALIBRATED)<sup>9+</sup>

on(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback&lt;AccelerometerUncalibratedResponse&gt;, options?: Options): void

订阅未校准加速度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onAccelerometerUncalibratedChange](#sensoronaccelerometeruncalibratedchange23)

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ACCELEROMETER_UNCALIBRATED            | 是   | 传感器类型，该值固定为SensorId.ACCELEROMETER_UNCALIBRATED。  |
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AccelerometerUncalibratedResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, (data: sensor.AccelerometerUncalibratedResponse) => {
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

## sensor.onAccelerometerUncalibratedChange<sup>23+</sup>

onAccelerometerUncalibratedChange(callback: Callback&lt;AccelerometerUncalibratedResponse&gt;, options?: Options): void

订阅未校准加速度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(ACCELEROMETER_UNCALIBRATED)](#sensoronaccelerometer_uncalibrated9)

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AccelerometerUncalibratedResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onAccelerometerUncalibratedChange((data: sensor.AccelerometerUncalibratedResponse) => {
    console.info('Succeeded in invoking onAccelerometerUncalibratedChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onAccelerometerUncalibratedChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onAccelerometerUncalibratedChange. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking onAccelerometerUncalibratedChange. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking onAccelerometerUncalibratedChange. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking onAccelerometerUncalibratedChange. Z-coordinate bias: ' + data.biasZ);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offAccelerometerUncalibratedChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onAccelerometerUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(AMBIENT_LIGHT)<sup>9+</sup>

on(type: SensorId.AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;, options?: Options): void

订阅环境光传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onAmbientLightChange](#sensoronambientlightchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                            | 必填 | 说明                                                        |
| -------- | ----------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).AMBIENT_LIGHT            | 是   | 传感器类型，该值固定为SensorId.AMBIENT_LIGHT。              |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为LightResponse。         |
| options  | [Options](#options)                             | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.AMBIENT_LIGHT, (data: sensor.LightResponse) => {
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

## sensor.onAmbientLightChange<sup>23+</sup>

onAmbientLightChange(callback: Callback&lt;LightResponse&gt;, options?: Options): void

订阅环境光传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(AMBIENT_LIGHT)](#sensoronambient_light9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                            | 必填 | 说明                                                        |
| -------- | ----------------------------------------------- | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为LightResponse。         |
| options  | [Options](#options)                             | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onAmbientLightChange((data: sensor.LightResponse) => {
    console.info('Succeeded in getting the ambient light intensity: ' + data.intensity);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offAmbientLightChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onAmbientLightChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(AMBIENT_TEMPERATURE)<sup>9+</sup>

on(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback&lt;AmbientTemperatureResponse&gt;, options?: Options): void

订阅温度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onAmbientTemperatureChange](#sensoronambienttemperaturechange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).AMBIENT_TEMPERATURE                   | 是   | 传感器类型，该值固定为SensorId.AMBIENT_TEMPERATURE。         |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AmbientTemperatureResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
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

## sensor.onAmbientTemperatureChange<sup>23+</sup>

onAmbientTemperatureChange(callback: Callback&lt;AmbientTemperatureResponse&gt;, options?: Options): void

订阅温度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(AMBIENT_TEMPERATURE)](#sensoronambient_temperature9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AmbientTemperatureResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onAmbientTemperatureChange((data: sensor.AmbientTemperatureResponse) => {
    console.info('Succeeded in invoking onAmbientTemperatureChange. Temperature: ' + data.temperature);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offAmbientTemperatureChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onAmbientTemperatureChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(BAROMETER)<sup>9+</sup>

on(type: SensorId.BAROMETER, callback: Callback&lt;BarometerResponse&gt;, options?: Options): void

订阅气压计传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onBarometerChange](#sensoronbarometerchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).BAROMETER                        | 是   | 传感器类型，该值固定为SensorId.BAROMETER。                  |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为BarometerResponse。     |
| options  | [Options](#options)                                     | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.BAROMETER, (data: sensor.BarometerResponse) => {
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

## sensor.onBarometerChange<sup>23+</sup>

onBarometerChange(callback: Callback&lt;BarometerResponse&gt;, options?: Options): void

订阅气压计传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(BAROMETER)](#sensoronbarometer9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为BarometerResponse。     |
| options  | [Options](#options)                                     | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onBarometerChange((data: sensor.BarometerResponse) => {
    console.info('Succeeded in invoking onBarometerChange. Atmospheric pressure: ' + data.pressure);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offBarometerChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onBarometerChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(GRAVITY)<sup>9+</sup>

on(type: SensorId.GRAVITY, callback: Callback&lt;GravityResponse&gt;, options?: Options): void

订阅重力传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onGravityChange](#sensorongravitychange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                | 必填 | 说明                                                        |
| -------- | --------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).GRAVITY                      | 是   | 传感器类型，该值固定为SensorId.GRAVITY。                    |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GravityResponse。       |
| options  | [Options](#options)                                 | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.GRAVITY, (data: sensor.GravityResponse) => {
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

## sensor.onGravityChange<sup>23+</sup>

onGravityChange(callback: Callback&lt;GravityResponse&gt;, options?: Options): void

订阅重力传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(GRAVITY)](#sensorongravity9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                | 必填 | 说明                                                        |
| -------- | --------------------------------------------------- | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GravityResponse。       |
| options  | [Options](#options)                                 | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onGravityChange((data: sensor.GravityResponse) => {
    console.info('Succeeded in invoking onGravityChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onGravityChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onGravityChange. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offGravityChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onGravityChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(GYROSCOPE)<sup>9+</sup>

on(type: SensorId.GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;, options?: Options): void

订阅校准的陀螺仪传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onGyroscopeChange](#sensorongyroscopechange23)

**需要权限**：ohos.permission.GYROSCOPE

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).GYROSCOPE                        | 是   | 传感器类型，该值固定为SensorId.GYROSCOPE。                  |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GyroscopeResponse。     |
| options  | [Options](#options)                                     | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.GYROSCOPE, (data: sensor.GyroscopeResponse) => {
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

## sensor.onGyroscopeChange<sup>23+</sup>

onGyroscopeChange(callback: Callback&lt;GyroscopeResponse&gt;, options?: Options): void

订阅校准的陀螺仪传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(GYROSCOPE)](#sensorongyroscope9)

**需要权限**：ohos.permission.GYROSCOPE

**原子化服务API**：从API Version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GyroscopeResponse。     |
| options  | [Options](#options)                                     | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onGyroscopeChange((data: sensor.GyroscopeResponse) => {
    console.info('Succeeded in invoking onGyroscopeChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onGyroscopeChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onGyroscopeChange. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offGyroscopeChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onGyroscopeChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(GYROSCOPE_UNCALIBRATED)<sup>9+</sup>

on(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback&lt;GyroscopeUncalibratedResponse&gt;,
      options?: Options): void

订阅未校准陀螺仪传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onGyroscopeUncalibratedChange](#sensorongyroscopeuncalibratedchange23)

**需要权限**：ohos.permission.GYROSCOPE 

**系统能力**：SystemCapability.Sensors.Sensor  

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).GYROSCOPE_UNCALIBRATED                | 是   | 传感器类型，该值固定为SensorId.GYROSCOPE_UNCALIBRATED。      |
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GyroscopeUncalibratedResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.GYROSCOPE_UNCALIBRATED, (data: sensor.GyroscopeUncalibratedResponse) => {
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

## sensor.onGyroscopeUncalibratedChange<sup>23+</sup>

onGyroscopeUncalibratedChange(callback: Callback&lt;GyroscopeUncalibratedResponse&gt;,
      options?: Options): void

订阅未校准陀螺仪传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(GYROSCOPE_UNCALIBRATED)](#sensorongyroscope_uncalibrated9)

**需要权限**：ohos.permission.GYROSCOPE 

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GyroscopeUncalibratedResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onGyroscopeUncalibratedChange((data: sensor.GyroscopeUncalibratedResponse) => {
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking onGyroscopeUncalibratedChange. Z-coordinate bias: ' + data.biasZ);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offGyroscopeUncalibratedChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onGyroscopeUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(HALL)<sup>9+</sup>

on(type: SensorId.HALL, callback: Callback&lt;HallResponse&gt;, options?: Options): void

订阅霍尔传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onHallChange](#sensoronhallchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                          | 必填 | 说明                                                         |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).HALL                   | 是   | 传感器类型，该值固定为SensorId.HALL。                        |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HallResponse。           |
| options  | [Options](#options)                           | 否   | 可选参数列表，默认值为200000000ns。当霍尔事件被触发的很频繁时，该参数用于限定事件上报的频率。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.HALL, (data: sensor.HallResponse) => {
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

## sensor.onHallChange<sup>23+</sup>

onHallChange(callback: Callback&lt;HallResponse&gt;, options?: Options): void

订阅霍尔传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(HALL)](#sensoronhall9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                          | 必填 | 说明                                                         |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HallResponse。           |
| options  | [Options](#options)                           | 否   | 可选参数列表，默认值为200000000ns。当霍尔事件被触发的很频繁时，该参数用于限定事件上报的频率。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.on(HEART_RATE)<sup>9+</sup>

on(type: SensorId.HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;, options?: Options): void

订阅心率传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onHeartRateChange](#sensoronheartratechange23)

**需要权限**：ohos.permission.READ_HEALTH_DATA 

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).HEART_RATE                       | 是   | 传感器类型，该值固定为SensorId.HEART_RATE。                 |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HeartRateResponse。     |
| options  | [Options](#options)                                     | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.HEART_RATE, (data: sensor.HeartRateResponse) => {
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

## sensor.onHeartRateChange<sup>23+</sup>

onHeartRateChange(callback: Callback&lt;HeartRateResponse&gt;, options?: Options): void

订阅心率传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(HEART_RATE)](#sensoronheart_rate9)

**需要权限**：ohos.permission.READ_HEALTH_DATA 

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HeartRateResponse。     |
| options  | [Options](#options)                                     | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onHeartRateChange((data: sensor.HeartRateResponse) => {
    console.info('Succeeded in invoking onHeartRateChange. Heart rate: ' + data.heartRate);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offHeartRateChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onHeartRateChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(HUMIDITY)<sup>9+</sup>

on(type: SensorId.HUMIDITY, callback: Callback&lt;HumidityResponse&gt;, options?: Options): void

订阅湿度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onHumidityChange](#sensoronhumiditychange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                  | 必填 | 说明                                                        |
| -------- | ----------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).HUMIDITY                       | 是   | 传感器类型，该值固定为SensorId.HUMIDITY。                   |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HumidityResponse。      |
| options  | [Options](#options)                                   | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.HUMIDITY, (data: sensor.HumidityResponse) => {
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

## sensor.onHumidityChange<sup>23+</sup>

onHumidityChange(callback: Callback&lt;HumidityResponse&gt;, options?: Options): void

订阅湿度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(HUMIDITY)](#sensoronhumidity9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                  | 必填 | 说明                                                        |
| -------- | ----------------------------------------------------- | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HumidityResponse。      |
| options  | [Options](#options)                                   | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onHumidityChange((data: sensor.HumidityResponse) => {
    console.info('Succeeded in invoking onHumidityChange. Humidity: ' + data.humidity);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offHumidityChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onHumidityChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(LINEAR_ACCELEROMETER)<sup>9+</sup>

on(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback&lt;LinearAccelerometerResponse&gt;,
        options?: Options): void

订阅线性加速度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onLinearAccelerometerChange](#sensoronlinearaccelerometerchange23)

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).LINEAR_ACCELEROMETER                  | 是   | 传感器类型，该值固定为SensorId.LINEAR_ACCELEROMETER。        |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为LinearAccelerometerResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.LINEAR_ACCELEROMETER, (data: sensor.LinearAccelerometerResponse) => {
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

## sensor.onLinearAccelerometerChange<sup>23+</sup>

onLinearAccelerometerChange(callback: Callback&lt;LinearAccelerometerResponse&gt;,
        options?: Options): void

订阅线性加速度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(LINEAR_ACCELEROMETER)](#sensoronlinear_accelerometer9)

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为LinearAccelerometerResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onLinearAccelerometerChange((data: sensor.LinearAccelerometerResponse) => {
    console.info('Succeeded in invoking onLinearAccelerometerChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onLinearAccelerometerChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onLinearAccelerometerChange. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offLinearAccelerometerChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onLinearAccelerometerChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(MAGNETIC_FIELD)<sup>9+</sup>

on(type: SensorId.MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;, options?: Options): void

订阅地磁传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onMagneticFieldChange](#sensoronmagneticfieldchange23)

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD                        | 是   | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD。             |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为MagneticFieldResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onMagneticFieldChange<sup>23+</sup>

onMagneticFieldChange(callback: Callback&lt;MagneticFieldResponse&gt;, options?: Options): void

订阅地磁传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(MAGNETIC_FIELD)](#sensoronmagnetic_field9)

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为MagneticFieldResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onMagneticFieldChange((data: sensor.MagneticFieldResponse) => {
    console.info('Succeeded in invoking onMagneticFieldChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onMagneticFieldChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onMagneticFieldChange. Z-coordinate component: ' + data.z);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offMagneticFieldChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onMagneticFieldChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(MAGNETIC_FIELD_UNCALIBRATED)<sup>9+</sup>

on(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;, options?: Options): void

订阅未校准地磁传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onMagneticFieldUncalibratedChange](#sensoronmagneticfielduncalibratedchange23)

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD_UNCALIBRATED           | 是   | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为MagneticFieldUncalibratedResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, (data: sensor.MagneticFieldUncalibratedResponse) => {
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

## sensor.onMagneticFieldUncalibratedChange<sup>23+</sup>

onMagneticFieldUncalibratedChange(callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;, options?: Options): void

订阅未校准地磁传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(MAGNETIC_FIELD_UNCALIBRATED)](#sensoronmagnetic_field_uncalibrated9)

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为MagneticFieldUncalibratedResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onMagneticFieldUncalibratedChange((data: sensor.MagneticFieldUncalibratedResponse) => {
    console.info('Succeeded in invoking onMagneticFieldUncalibratedChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onMagneticFieldUncalibratedChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onMagneticFieldUncalibratedChange. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking onMagneticFieldUncalibratedChange. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking onMagneticFieldUncalibratedChange. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking onMagneticFieldUncalibratedChange. Z-coordinate bias: ' + data.biasZ);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offMagneticFieldUncalibratedChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onMagneticFieldUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(ORIENTATION)<sup>9+</sup>

on(type: SensorId.ORIENTATION, callback: Callback&lt;OrientationResponse&gt;, options?: Options): void

订阅方向传感器数据。

> **说明：**
> 
> 调用本接口的应用或服务可以通过提示用户使用8字校准法来提高应用获取的方向传感器的精度，此传感器理论误差正负5度，具体的精度根据不同的驱动及算法实现可能存在差异。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onOrientationChange](#sensoronorientationchange23)

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**参数**：

| 参数名   | 类型                                                        | 必填 | 说明                                                        |
| -------- | ----------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).ORIENTATION                          | 是   | 传感器类型，该值固定为SensorId.ORIENTATION。                |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为OrientationResponse。   |
| options  | [Options](#options)                                         | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.ORIENTATION, (data: sensor.OrientationResponse) => {
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

## sensor.onOrientationChange<sup>23+</sup>

onOrientationChange(callback: Callback&lt;OrientationResponse&gt;, options?: Options): void

订阅方向传感器数据。

> **说明：**
> 
> 调用本接口的应用或服务可以通过提示用户使用8字校准法来提高应用获取的方向传感器的精度，此传感器理论误差正负5度，具体的精度根据不同的驱动及算法实现可能存在差异。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(ORIENTATION)](#sensoronorientation9)

**原子化服务API**：从API Version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**参数**：

| 参数名   | 类型                                                        | 必填 | 说明                                                        |
| -------- | ----------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为OrientationResponse。   |
| options  | [Options](#options)                                         | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onOrientationChange((data: sensor.OrientationResponse) => {
    console.info('Succeeded in the device rotating at an angle around the Z axis: ' + data.alpha);
    console.info('Succeeded in the device rotating at an angle around the X axis: ' + data.beta);
    console.info('Succeeded in the device rotating at an angle around the Y axis: ' + data.gamma);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offOrientationChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onOrientationChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(PEDOMETER)<sup>9+</sup>

on(type: SensorId.PEDOMETER, callback: Callback&lt;PedometerResponse&gt;, options?: Options): void

订阅计步器传感器数据。计步传感器数据上报有一定延迟，延迟时间由具体的实现产品决定。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onPedometerChange](#sensoronpedometerchange23)

**需要权限**：ohos.permission.ACTIVITY_MOTION 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).PEDOMETER                        | 是   | 传感器类型，该值固定为SensorId.PEDOMETER。                  |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为PedometerResponse。     |
| options  | [Options](#options)                                     | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.PEDOMETER, (data: sensor.PedometerResponse) => {
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

## sensor.onPedometerChange<sup>23+</sup>

onPedometerChange(callback: Callback&lt;PedometerResponse&gt;, options?: Options): void

订阅计步器传感器数据。计步传感器数据上报有一定延迟，延迟时间由具体的实现产品决定。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(PEDOMETER)](#sensoronpedometer9)

**需要权限**：ohos.permission.ACTIVITY_MOTION 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为PedometerResponse。     |
| options  | [Options](#options)                                     | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onPedometerChange((data: sensor.PedometerResponse) => {
    console.info('Succeeded in invoking onPedometerChange. Step count: ' + data.steps);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offPedometerChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onPedometerChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(PEDOMETER_DETECTION)<sup>9+</sup>

on(type: SensorId.PEDOMETER_DETECTION, callback: Callback&lt;PedometerDetectionResponse&gt;,
        options?: Options): void

订阅计步检测器传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onPedometerDetectionChange](#sensoronpedometerdetectionchange23)

**需要权限**：ohos.permission.ACTIVITY_MOTION 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PEDOMETER_DETECTION                   | 是   | 传感器类型，该值固定为SensorId.PEDOMETER_DETECTION。         |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为PedometerDetectionResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
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

## sensor.onPedometerDetectionChange<sup>23+</sup>

onPedometerDetectionChange(callback: Callback&lt;PedometerDetectionResponse&gt;,
        options?: Options): void

订阅计步检测器传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(PEDOMETER_DETECTION)](#sensoronpedometer_detection9)

**需要权限**：ohos.permission.ACTIVITY_MOTION 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为PedometerDetectionResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onPedometerDetectionChange((data: sensor.PedometerDetectionResponse) => {
    console.info('Succeeded in invoking onPedometerDetectionChange. Pedometer scalar: ' + data.scalar);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offPedometerDetectionChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onPedometerDetectionChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(PROXIMITY)<sup>9+</sup>

on(type: SensorId.PROXIMITY, callback: Callback&lt;ProximityResponse&gt;, options?: Options): void

订阅接近光传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onProximityChange](#sensoronproximitychange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PROXIMITY                        | 是   | 传感器类型，该值固定为SensorId.PROXIMITY。                   |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为ProximityResponse。      |
| options  | [Options](#options)                                     | 否   | 可选参数列表，默认值为200000000ns。当接近光事件被触发的很频繁时，该参数用于限定事件上报的频率。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3.Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.PROXIMITY, (data: sensor.ProximityResponse) => {
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

## sensor.onProximityChange<sup>23+</sup>

onProximityChange(callback: Callback&lt;ProximityResponse&gt;, options?: Options): void

订阅接近光传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(PROXIMITY)](#sensoronproximity9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为ProximityResponse。      |
| options  | [Options](#options)                                     | 否   | 可选参数列表，默认值为200000000ns。当接近光事件被触发的很频繁时，该参数用于限定事件上报的频率。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onProximityChange((data: sensor.ProximityResponse) => {
    console.info('Succeeded in invoking onProximityChange. Distance: ' + data.distance);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offProximityChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onProximityChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(ROTATION_VECTOR)<sup>9+</sup>

on(type: SensorId.ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;,
        options?: Options): void

订阅旋转矢量传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onRotationVectorChange](#sensoronrotationvectorchange23)

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ROTATION_VECTOR                       | 是   | 传感器类型，该值固定为SensorId.ROTATION_VECTOR。             |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为RotationVectorResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3.Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onRotationVectorChange<sup>23+</sup>

onRotationVectorChange(callback: Callback&lt;RotationVectorResponse&gt;,
        options?: Options): void

订阅旋转矢量传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(ROTATION_VECTOR)](#sensoronrotation_vector9)

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为RotationVectorResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onRotationVectorChange((data: sensor.RotationVectorResponse) => {
    console.info('Succeeded in invoking onRotationVectorChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onRotationVectorChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onRotationVectorChange. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking onRotationVectorChange. Scalar quantity: ' + data.w);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offRotationVectorChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onRotationVectorChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on(SIGNIFICANT_MOTION)<sup>9+</sup>

on(type: SensorId.SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;,
        options?: Options): void

订阅有效运动传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onSignificantMotionChange](#sensoronsignificantmotionchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).SIGNIFICANT_MOTION                    | 是   | 传感器类型，该值固定为SensorId.SIGNIFICANT_MOTION。          |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为SignificantMotionResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3.Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onSignificantMotionChange<sup>23+</sup>

onSignificantMotionChange(callback: Callback&lt;SignificantMotionResponse&gt;,
        options?: Options): void

订阅有效运动传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(SIGNIFICANT_MOTION)](#sensoronsignificant_motion9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为SignificantMotionResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.on(WEAR_DETECTION)<sup>9+</sup>

on(type: SensorId.WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;,
        options?: Options): void

订阅佩戴检测传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onWearDetectionChange](#sensoronweardetectionchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).WEAR_DETECTION                        | 是   | 传感器类型，该值固定为SensorId.WEAR_DETECTION。             |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为WearDetectionResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3.Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onWearDetectionChange<sup>23+</sup>

onWearDetectionChange(callback: Callback&lt;WearDetectionResponse&gt;, options?: Options): void

订阅佩戴检测传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[on(WEAR_DETECTION)](#sensoronwear_detection9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为WearDetectionResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onWearDetectionChange((data: sensor.WearDetectionResponse) => {
    console.info('Succeeded in invoking onWearDetectionChange. Wear status: ' + data.value);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.offWearDetectionChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onWearDetectionChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.on('sensorStatusChange')<sup>19+</sup>

on(type: 'sensorStatusChange', callback: Callback&lt;SensorStatusEvent&gt;): void

监听传感器上线下线状态的变化，callback返回传感器状态事件数据。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| sensorStatusChange     |  固定传入'sensorStatusChange'         | 是   | 状态监听固定参数。             |
| callback | Callback&lt;[SensorStatusEvent](#sensorstatusevent19)&gt; | 是   | 回调函数，异步上报的传感器事件数据SensorStatusEvent。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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


## sensor.once(ACCELEROMETER)<sup>9+</sup>

once(type: SensorId.ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;): void

获取一次加速度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceAccelerometerChange](#sensoronceaccelerometerchange23)

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).ACCELEROMETER                         | 是   | 传感器类型，该值固定为SensorId.ACCELEROMETER。              |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AccelerometerResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceAccelerometerChange<sup>23+</sup>

onceAccelerometerChange(callback: Callback&lt;AccelerometerResponse&gt;): void

获取一次加速度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(ACCELEROMETER)](#sensoronceaccelerometer9)

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AccelerometerResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceAccelerometerChange((data: sensor.AccelerometerResponse) => {
    console.info('Succeeded in invoking onceAccelerometerChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onceAccelerometerChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onceAccelerometerChange. Z-coordinate component: ' + data.z);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceAccelerometerChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(ACCELEROMETER_UNCALIBRATED)<sup>9+</sup>

once(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

获取一次未校准加速度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceAccelerometerUncalibratedChange](#sensoronceaccelerometeruncalibratedchange23)

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ACCELEROMETER_UNCALIBRATED            | 是   | 传感器类型，该值固定为SensorId.ACCELEROMETER_UNCALIBRATED。  |
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AccelerometerUncalibratedResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceAccelerometerUncalibratedChange<sup>23+</sup>

onceAccelerometerUncalibratedChange(callback: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

获取一次未校准加速度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(ACCELEROMETER_UNCALIBRATED)](#sensoronceaccelerometer_uncalibrated9)

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AccelerometerUncalibratedResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceAccelerometerUncalibratedChange((data: sensor.AccelerometerUncalibratedResponse) => {
    console.info('Succeeded in invoking onceAccelerometerUncalibratedChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onceAccelerometerUncalibratedChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onceAccelerometerUncalibratedChange. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking onceAccelerometerUncalibratedChange. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking onceAccelerometerUncalibratedChange. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking onceAccelerometerUncalibratedChange. Z-coordinate bias: ' + data.biasZ);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceAccelerometerUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(AMBIENT_LIGHT)<sup>9+</sup>

once(type: SensorId.AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;): void

获取一次环境光传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceAmbientLightChange](#sensoronceambientlightchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                            | 必填 | 说明                                                |
| -------- | ----------------------------------------------- | ---- | --------------------------------------------------- |
| type     | [SensorId](#sensorid9).AMBIENT_LIGHT            | 是   | 传感器类型，该值固定为SensorId.AMBIENT_LIGHT。      |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为LightResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceAmbientLightChange<sup>23+</sup>

onceAmbientLightChange(callback: Callback&lt;LightResponse&gt;): void

获取一次环境光传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(AMBIENT_LIGHT)](#sensoronceambient_light9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                            | 必填 | 说明                                                |
| -------- | ----------------------------------------------- | ---- | --------------------------------------------------- |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为LightResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceAmbientLightChange((data: sensor.LightResponse) => {
    console.info('Succeeded in invoking onceAmbientLightChange. the ambient light intensity: ' + data.intensity);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceAmbientLightChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(AMBIENT_TEMPERATURE)<sup>9+</sup>

once(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback&lt;AmbientTemperatureResponse&gt;): void

获取一次温度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceAmbientTemperatureChange](#sensoronceambienttemperaturechange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).AMBIENT_TEMPERATURE                   | 是   | 传感器类型，该值固定为SensorId.AMBIENT_TEMPERATURE。         |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AmbientTemperatureResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceAmbientTemperatureChange<sup>23+</sup>

onceAmbientTemperatureChange(callback: Callback&lt;AmbientTemperatureResponse&gt;): void

获取一次温度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(AMBIENT_TEMPERATURE)](#sensoronceambient_temperature9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为AmbientTemperatureResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceAmbientTemperatureChange((data: sensor.AmbientTemperatureResponse) => {
    console.info('Succeeded in invoking onceAmbientTemperatureChange. Temperature: ' + data.temperature);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceAmbientTemperatureChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(BAROMETER)<sup>9+</sup>

once(type: SensorId.BAROMETER, callback: Callback&lt;BarometerResponse&gt;): void

获取一次气压计传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceBarometerChange](#sensoroncebarometerchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                    |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| type     | [SensorId](#sensorid9).BAROMETER                        | 是   | 传感器类型，该值固定为SensorId.BAROMETER。              |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为BarometerResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceBarometerChange<sup>23+</sup>

onceBarometerChange(callback: Callback&lt;BarometerResponse&gt;): void

获取一次气压计传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(BAROMETER)](#sensoroncebarometer9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                    |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为BarometerResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceBarometerChange((data: sensor.BarometerResponse) => {
    console.info('Succeeded in invoking onceBarometerChange. Atmospheric pressure: ' + data.pressure);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceBarometerChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(GRAVITY)<sup>9+</sup>

once(type: SensorId.GRAVITY, callback: Callback&lt;GravityResponse&gt;): void

获取一次重力传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceGravityChange](#sensoroncegravitychange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                | 必填 | 说明                                                  |
| -------- | --------------------------------------------------- | ---- | ----------------------------------------------------- |
| type     | [SensorId](#sensorid9).GRAVITY                      | 是   | 传感器类型，该值固定为SensorId.GRAVITY。              |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GravityResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceGravityChange<sup>23+</sup>

onceGravityChange(callback: Callback&lt;GravityResponse&gt;): void

获取一次重力传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(GRAVITY)](#sensoroncegravity9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                | 必填 | 说明                                                  |
| -------- | --------------------------------------------------- | ---- | ----------------------------------------------------- |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GravityResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceGravityChange((data: sensor.GravityResponse) => {
    console.info('Succeeded in invoking onceGravityChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onceGravityChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onceGravityChange. Z-coordinate component: ' + data.z);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceGravityChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(GYROSCOPE)<sup>9+</sup>

once(type: SensorId.GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;): void

获取一次陀螺仪传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceGyroscopeChange](#sensoroncegyroscopechange23)

**需要权限**：ohos.permission.GYROSCOPE 

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                    |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| type     | [SensorId](#sensorid9).GYROSCOPE                        | 是   | 传感器类型，该值固定为SensorId.GYROSCOPE。              |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GyroscopeResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceGyroscopeChange<sup>23+</sup>

onceGyroscopeChange(callback: Callback&lt;GyroscopeResponse&gt;): void

获取一次陀螺仪传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(GYROSCOPE)](#sensoroncegyroscope9)

**需要权限**：ohos.permission.GYROSCOPE 

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                    |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GyroscopeResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceGyroscopeChange((data: sensor.GyroscopeResponse) => {
    console.info('Succeeded in invoking onceGyroscopeChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onceGyroscopeChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onceGyroscopeChange. Z-coordinate component: ' + data.z);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceGyroscopeChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(GYROSCOPE_UNCALIBRATED)<sup>9+</sup>

once(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

获取一次未校准陀螺仪传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceGyroscopeUncalibratedChange](#sensoroncegyroscopeuncalibratedchange23)

**需要权限**：ohos.permission.GYROSCOPE

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).GYROSCOPE_UNCALIBRATED                | 是   | 传感器类型，该值固定为SensorId.GYROSCOPE_UNCALIBRATED。      |
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GyroscopeUncalibratedResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceGyroscopeUncalibratedChange<sup>23+</sup>

onceGyroscopeUncalibratedChange(callback: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

获取一次未校准陀螺仪传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(GYROSCOPE_UNCALIBRATED)](#sensoroncegyroscope_uncalibrated9)

**需要权限**：ohos.permission.GYROSCOPE

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为GyroscopeUncalibratedResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceGyroscopeUncalibratedChange((data: sensor.GyroscopeUncalibratedResponse) => {
    console.info('Succeeded in invoking onceGyroscopeUncalibratedChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onceGyroscopeUncalibratedChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onceGyroscopeUncalibratedChange. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking onceGyroscopeUncalibratedChange. X-coordinate bias: ' + data.biasX);
    console.info('Succeeded in invoking onceGyroscopeUncalibratedChange. Y-coordinate bias: ' + data.biasY);
    console.info('Succeeded in invoking onceGyroscopeUncalibratedChange. Z-coordinate bias: ' + data.biasZ);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceGyroscopeUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(HALL)<sup>9+</sup>

once(type: SensorId.HALL, callback: Callback&lt;HallResponse&gt;): void

获取一次霍尔传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceHallChange](#sensoroncehallchange23)

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                          | 必填 | 说明                                               |
| -------- | --------------------------------------------- | ---- | -------------------------------------------------- |
| type     | [SensorId](#sensorid9).HALL                   | 是   | 传感器类型，该值固定为SensorId.HALL。              |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HallResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceHallChange<sup>23+</sup>

onceHallChange(callback: Callback&lt;HallResponse&gt;): void

获取一次霍尔传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(HALL)](#sensoroncehall9)

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                          | 必填 | 说明                                               |
| -------- | --------------------------------------------- | ---- | -------------------------------------------------- |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HallResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceHallChange((data: sensor.HallResponse) => {
    console.info('Succeeded in invoking onceHallChange. Status: ' + data.status);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceHallChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(HEART_RATE)<sup>9+</sup>

once(type: SensorId.HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;): void

获取一次心率传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceHeartRateChange](#sensoronceheartratechange23)

**需要权限**：ohos.permission.READ_HEALTH_DATA 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                    |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| type     | [SensorId](#sensorid9).HEART_RATE                       | 是   | 传感器类型，该值固定为SensorId.HEART_RATE。             |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HeartRateResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceHeartRateChange<sup>23+</sup>

onceHeartRateChange(callback: Callback&lt;HeartRateResponse&gt;): void

获取一次心率传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(HEART_RATE)](#sensoronceheart_rate9)

**需要权限**：ohos.permission.READ_HEALTH_DATA 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                    |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HeartRateResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceHeartRateChange((data: sensor.HeartRateResponse) => {
    console.info('Succeeded in invoking onceHeartRateChange. Heart rate: ' + data.heartRate);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceHeartRateChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(HUMIDITY)<sup>9+</sup>

once(type: SensorId.HUMIDITY, callback: Callback&lt;HumidityResponse&gt;): void

获取一次湿度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceHumidityChange](#sensoroncehumiditychange23)

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                  | 必填 | 说明                                                   |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------ |
| type     | [SensorId](#sensorid9).HUMIDITY                       | 是   | 传感器类型，该值固定为SensorId.HUMIDITY。              |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HumidityResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceHumidityChange<sup>23+</sup>

onceHumidityChange(callback: Callback&lt;HumidityResponse&gt;): void

获取一次湿度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(HUMIDITY)](#sensoroncehumidity9)

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                  | 必填 | 说明                                                   |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------ |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为HumidityResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceHumidityChange((data: sensor.HumidityResponse) => {
    console.info('Succeeded in invoking onceHumidityChange. Humidity: ' + data.humidity);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceHumidityChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(LINEAR_ACCELEROMETER)<sup>9+</sup>

once(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback&lt;LinearAccelerometerResponse&gt;): void

获取一次线性加速度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceLinearAccelerometerChange](#sensoroncelinearaccelerometerchange23)

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).LINEAR_ACCELEROMETER                  | 是   | 传感器类型，该值固定为SensorId.LINEAR_ACCELEROMETER。        |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为LinearAccelerometerResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceLinearAccelerometerChange<sup>23+</sup>

onceLinearAccelerometerChange(callback: Callback&lt;LinearAccelerometerResponse&gt;): void

获取一次线性加速度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(LINEAR_ACCELEROMETER)](#sensoroncelinear_accelerometer9)

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为LinearAccelerometerResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceLinearAccelerometerChange((data: sensor.LinearAccelerometerResponse) => {
    console.info('Succeeded in invoking onceLinearAccelerometerChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onceLinearAccelerometerChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onceLinearAccelerometerChange. Z-coordinate component: ' + data.z);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceLinearAccelerometerChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(MAGNETIC_FIELD)<sup>9+</sup>

once(type: SensorId.MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;): void

获取一次磁场传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceMagneticFieldChange](#sensoroncemagneticfieldchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD                        | 是   | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD。             |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为MagneticFieldResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceMagneticFieldChange<sup>23+</sup>

onceMagneticFieldChange(callback: Callback&lt;MagneticFieldResponse&gt;): void

获取一次磁场传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(MAGNETIC_FIELD)](#sensoroncemagnetic_field9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为MagneticFieldResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.once(MAGNETIC_FIELD_UNCALIBRATED)<sup>9+</sup>

once(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

获取一次未经校准的磁场传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceMagneticFieldUncalibratedChange](#sensoroncemagneticfielduncalibratedchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD_UNCALIBRATED           | 是   | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为MagneticFieldUncalibratedResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceMagneticFieldUncalibratedChange<sup>23+</sup>

onceMagneticFieldUncalibratedChange(callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

获取一次未经校准的磁场传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(MAGNETIC_FIELD_UNCALIBRATED)](#sensoroncemagnetic_field_uncalibrated9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为MagneticFieldUncalibratedResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.once(ORIENTATION)<sup>9+</sup>

once(type: SensorId.ORIENTATION, callback: Callback&lt;OrientationResponse&gt;): void

获取一次方向传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceOrientationChange](#sensoronceorientationchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                        | 必填 | 说明                                                      |
| -------- | ----------------------------------------------------------- | ---- | --------------------------------------------------------- |
| type     | [SensorId](#sensorid9).ORIENTATION                          | 是   | 传感器类型，该值固定为SensorId.ORIENTATION。              |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为OrientationResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceOrientationChange<sup>23+</sup>

onceOrientationChange(callback: Callback&lt;OrientationResponse&gt;): void

获取一次方向传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(ORIENTATION)](#sensoronceorientation9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                        | 必填 | 说明                                                      |
| -------- | ----------------------------------------------------------- | ---- | --------------------------------------------------------- |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为OrientationResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceOrientationChange((data: sensor.OrientationResponse) => {
    console.info('Succeeded in the device rotating at an angle around the X axis: ' + data.beta);
    console.info('Succeeded in the device rotating at an angle around the Y axis: ' + data.gamma);
    console.info('Succeeded in the device rotating at an angle around the Z axis: ' + data.alpha);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceOrientationChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(PEDOMETER)<sup>9+</sup>

once(type: SensorId.PEDOMETER, callback: Callback&lt;PedometerResponse&gt;): void

获取一次计步器传感器数据。计步传感器数据上报有一定延迟，延迟时间由具体的实现产品决定。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[oncePedometerChange](#sensoroncepedometerchange23)

**需要权限**：ohos.permission.ACTIVITY_MOTION 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                    |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| type     | [SensorId](#sensorid9).PEDOMETER                        | 是   | 传感器类型，该值固定为SensorId.PEDOMETER。              |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为PedometerResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.oncePedometerChange<sup>23+</sup>

oncePedometerChange(callback: Callback&lt;PedometerResponse&gt;): void

获取一次计步器传感器数据。计步传感器数据上报有一定延迟，延迟时间由具体的实现产品决定。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(PEDOMETER)](#sensoroncepedometer9)

**需要权限**：ohos.permission.ACTIVITY_MOTION 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                    |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为PedometerResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.oncePedometerChange((data: sensor.PedometerResponse) => {
    console.info('Succeeded in invoking oncePedometerChange. Step count: ' + data.steps);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke oncePedometerChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(PEDOMETER_DETECTION)<sup>9+</sup>

once(type: SensorId.PEDOMETER_DETECTION, callback: Callback&lt;PedometerDetectionResponse&gt;): void

获取一次计步检测器传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[oncePedometerDetectionChange](#sensoroncepedometerdetectionchange23)

**系需要权限**：ohos.permission.ACTIVITY_MOTION 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PEDOMETER_DETECTION                   | 是   | 传感器类型，该值固定为SensorId.PEDOMETER_DETECTION。         |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为PedometerDetectionResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.oncePedometerDetectionChange<sup>23+</sup>

oncePedometerDetectionChange(callback: Callback&lt;PedometerDetectionResponse&gt;): void

获取一次计步检测器传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(PEDOMETER_DETECTION)](#sensoroncepedometer_detection9)

**系需要权限**：ohos.permission.ACTIVITY_MOTION 

**系统能力**：SystemCapability.Sensors.Sensor 

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为PedometerDetectionResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.oncePedometerDetectionChange((data: sensor.PedometerDetectionResponse) => {
    console.info('Succeeded in invoking oncePedometerDetectionChange. Scalar data: ' + data.scalar);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke oncePedometerDetectionChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(PROXIMITY)<sup>9+</sup>

once(type: SensorId.PROXIMITY, callback: Callback&lt;ProximityResponse&gt;): void

获取一次接近光传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceProximityChange](#sensoronceproximitychange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                    |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| type     | [SensorId](#sensorid9).PROXIMITY                        | 是   | 传感器类型，该值固定为SensorId.PROXIMITY。              |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为ProximityResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceProximityChange<sup>23+</sup>

onceProximityChange(callback: Callback&lt;ProximityResponse&gt;): void

获取一次接近光传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(PROXIMITY)](#sensoronceproximity9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                    |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为ProximityResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceProximityChange((data: sensor.ProximityResponse) => {
    console.info('Succeeded in invoking onceProximityChange. Distance: ' + data.distance);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceProximityChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(ROTATION_VECTOR)<sup>9+</sup>

once(type: SensorId.ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;): void

获取一次旋转矢量传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceRotationVectorChange](#sensoroncerotationvectorchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ROTATION_VECTOR                       | 是   | 传感器类型，该值固定为SensorId.ROTATION_VECTOR。             |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为RotationVectorResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceRotationVectorChange<sup>23+</sup>

onceRotationVectorChange(callback: Callback&lt;RotationVectorResponse&gt;): void

获取一次旋转矢量传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(ROTATION_VECTOR)](#sensoroncerotation_vector9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为RotationVectorResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceRotationVectorChange((data: sensor.RotationVectorResponse) => {
    console.info('Succeeded in invoking onceRotationVectorChange. X-coordinate component: ' + data.x);
    console.info('Succeeded in invoking onceRotationVectorChange. Y-coordinate component: ' + data.y);
    console.info('Succeeded in invoking onceRotationVectorChange. Z-coordinate component: ' + data.z);
    console.info('Succeeded in invoking onceRotationVectorChange. Scalar quantity: ' + data.w);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceRotationVectorChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(SIGNIFICANT_MOTION)<sup>9+</sup>

once(type: SensorId.SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;): void

获取一次有效运动传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceSignificantMotionChange](#sensoroncesignificantmotionchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).SIGNIFICANT_MOTION                    | 是   | 传感器类型，该值固定为SensorId.SIGNIFICANT_MOTION。          |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为SignificantMotionResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceSignificantMotionChange<sup>23+</sup>

onceSignificantMotionChange(callback: Callback&lt;SignificantMotionResponse&gt;): void

获取一次有效运动传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(SIGNIFICANT_MOTION)](#sensoroncesignificant_motion9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为SignificantMotionResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.onceSignificantMotionChange((data: sensor.SignificantMotionResponse) => {
    console.info('Succeeded in invoking onceSignificantMotionChange. Scalar data: ' + data.scalar);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onceSignificantMotionChange. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once(WEAR_DETECTION)<sup>9+</sup>

once(type: SensorId.WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;): void

获取一次佩戴检测传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[onceWearDetectionChange](#sensoronceweardetectionchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).WEAR_DETECTION                        | 是   | 传感器类型，该值固定为SensorId.WEAR_DETECTION。             |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为WearDetectionResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.onceWearDetectionChange<sup>23+</sup>

onceWearDetectionChange(callback: Callback&lt;WearDetectionResponse&gt;): void

获取一次佩戴检测传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[once(WEAR_DETECTION)](#sensoroncewear_detection9)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | 是   | 回调函数，异步上报的传感器数据固定为WearDetectionResponse。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
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

## sensor.off(ACCELEROMETER)<sup>9+</sup> 

off(type: SensorId.ACCELEROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;AccelerometerResponse&gt;): void

取消订阅加速度传感器数据。

**需要权限**：ohos.permission.ACCELEROMETER

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名                           | 类型                                                         | 必填 | 说明                                                         |
|-------------------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type                          | [SensorId](#sensorid9).ACCELEROMETER                         | 是   | 传感器类型，该值固定为SensorId.ACCELEROMETER。               |
| sensorInfoParam<sup>19+</sup> | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback                      | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.ACCELEROMETER, callback1);
  sensor.on(sensor.SensorId.ACCELEROMETER, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.ACCELEROMETER, callback1);
  // 取消SensorId.ACCELEROMETER类型的所有回调
  sensor.off(sensor.SensorId.ACCELEROMETER);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(ACCELEROMETER)<sup>19+</sup>

off(type: SensorId.ACCELEROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;AccelerometerResponse&gt;): void

取消订阅加速度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offAccelerometerChange](#sensoroffaccelerometerchange23)

**需要权限**：ohos.permission.ACCELEROMETER

**原子化服务API**：从API Version 19开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名                | 类型                                                         | 必填 | 说明                                                         |
|--------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type               | [SensorId](#sensorid9).ACCELEROMETER                         | 是   | 传感器类型，该值固定为SensorId.ACCELEROMETER。               |
| sensorInfoParam    | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback           | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.AccelerometerResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类别
const sensorType = sensor.SensorId.ACCELEROMETER;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offAccelerometerChange<sup>23+</sup>

offAccelerometerChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;AccelerometerResponse&gt;): void

取消订阅加速度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(ACCELEROMETER)](#sensoroffaccelerometer19)

**需要权限**：ohos.permission.ACCELEROMETER

**原子化服务API**：从API Version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名                | 类型                                                         | 必填 | 说明                                                         |
|--------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensorInfoParam    | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback           | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.AccelerometerResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onAccelerometerChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onAccelerometerChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offAccelerometerChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offAccelerometerChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(ACCELEROMETER_UNCALIBRATED)<sup>9+</sup>  

off(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback?: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

取消订阅未校准加速度传感器数据。

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ACCELEROMETER_UNCALIBRATED            | 是   | 传感器类型，该值固定为SensorId.ACCELEROMETER_UNCALIBRATED。  |
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, callback1);
  sensor.on(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, callback1);
  // 取消注册SensorId.ACCELEROMETER_UNCALIBRATED类型的所有回调
  sensor.off(sensor.SensorId.ACCELEROMETER_UNCALIBRATED);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(ACCELEROMETER_UNCALIBRATED)<sup>19+</sup>

off(type: SensorId.ACCELEROMETER_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

取消订阅未校准加速度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offAccelerometerUncalibratedChange](#sensoroffaccelerometeruncalibratedchange23)

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).ACCELEROMETER_UNCALIBRATED            | 是   | 传感器类型，该值固定为SensorId.ACCELEROMETER_UNCALIBRATED。  |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.AccelerometerUncalibratedResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.ACCELEROMETER_UNCALIBRATED;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offAccelerometerUncalibratedChange<sup>23+</sup>

offAccelerometerUncalibratedChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

取消订阅未校准加速度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(ACCELEROMETER_UNCALIBRATED)](#sensoroffaccelerometer_uncalibrated19)

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.AccelerometerUncalibratedResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onAccelerometerUncalibratedChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onAccelerometerUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offAccelerometerUncalibratedChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offAccelerometerUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(AMBIENT_LIGHT)<sup>9+</sup> 

off(type: SensorId.AMBIENT_LIGHT, callback?: Callback&lt;LightResponse&gt;): void

取消订阅环境光传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                            | 必填 | 说明                                                         |
| -------- | ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).AMBIENT_LIGHT            | 是   | 传感器类型，该值固定为SensorId.AMBIENT_LIGHT。               |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.AMBIENT_LIGHT, callback1);
  sensor.on(sensor.SensorId.AMBIENT_LIGHT, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.AMBIENT_LIGHT, callback1);
  // 取消注册SensorId.AMBIENT_LIGHT
  sensor.off(sensor.SensorId.AMBIENT_LIGHT);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(AMBIENT_LIGHT)<sup>19+</sup>

off(type: SensorId.AMBIENT_LIGHT, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;LightResponse&gt;): void

取消订阅环境光传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offAmbientLightChange](#sensoroffambientlightchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                            | 必填 | 说明                                                         |
|------------------| ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).AMBIENT_LIGHT            | 是   | 传感器类型，该值固定为SensorId.AMBIENT_LIGHT。               |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[LightResponse](#lightresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.LightResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.AMBIENT_LIGHT;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offAmbientLightChange<sup>23+</sup>

offAmbientLightChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;LightResponse&gt;): void

取消订阅环境光传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(AMBIENT_LIGHT)](#sensoroffambient_light19)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                            | 必填 | 说明                                                         |
|------------------| ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[LightResponse](#lightresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.LightResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onAmbientLightChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onAmbientLightChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offAmbientLightChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offAmbientLightChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(AMBIENT_TEMPERATURE)<sup>9+</sup> 

off(type: SensorId.AMBIENT_TEMPERATURE, callback?: Callback&lt;AmbientTemperatureResponse&gt;): void

取消订阅温度传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).AMBIENT_TEMPERATURE                   | 是   | 传感器类型，该值固定为SensorId.AMBIENT_TEMPERATURE。         |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.AMBIENT_TEMPERATURE, callback1);
  sensor.on(sensor.SensorId.AMBIENT_TEMPERATURE, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.AMBIENT_TEMPERATURE, callback1);
  // 取消注册SensorId.AMBIENT_TEMPERATURE的所有回调
  sensor.off(sensor.SensorId.AMBIENT_TEMPERATURE);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(AMBIENT_TEMPERATURE)<sup>19+</sup>

off(type: SensorId.AMBIENT_TEMPERATURE, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;AmbientTemperatureResponse&gt;): void

取消订阅温度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offAmbientTemperatureChange](#sensoroffambienttemperaturechange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).AMBIENT_TEMPERATURE                   | 是   | 传感器类型，该值固定为SensorId.AMBIENT_TEMPERATURE。         |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.AmbientTemperatureResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.AMBIENT_TEMPERATURE;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offAmbientTemperatureChange<sup>23+</sup>

offAmbientTemperatureChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;AmbientTemperatureResponse&gt;): void

取消订阅温度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(AMBIENT_TEMPERATURE)](#sensoroffambient_temperature19)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.AmbientTemperatureResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onAmbientTemperatureChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onAmbientTemperatureChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offAmbientTemperatureChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offAmbientTemperatureChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(BAROMETER)<sup>9+</sup>  

off(type: SensorId.BAROMETER, callback?: Callback&lt;BarometerResponse&gt;): void

取消订阅气压计传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).BAROMETER                        | 是   | 传感器类型，该值固定为SensorId.BAROMETER。                   |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
    console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
    console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
    sensor.on(sensor.SensorId.BAROMETER, callback1);
    sensor.on(sensor.SensorId.BAROMETER, callback2);
    // 仅取消callback1的注册
    sensor.off(sensor.SensorId.BAROMETER, callback1);
    // 取消注册SensorId.BAROMETER的所有回调
    sensor.off(sensor.SensorId.BAROMETER);
} catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(BAROMETER)<sup>19+</sup>

off(type: SensorId.BAROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;BarometerResponse&gt;): void

取消订阅气压计传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offBarometerChange](#sensoroffbarometerchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                    | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).BAROMETER                        | 是   | 传感器类型，该值固定为SensorId.BAROMETER。                   |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[BarometerResponse](#barometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.BarometerResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.BAROMETER;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offBarometerChange<sup>23+</sup>

offBarometerChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;BarometerResponse&gt;): void

取消订阅气压计传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(BAROMETER)](#sensoroffbarometer19)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                    | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[BarometerResponse](#barometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.BarometerResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onBarometerChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onBarometerChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offBarometerChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offBarometerChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(GRAVITY)<sup>9+</sup> 

off(type: SensorId.GRAVITY, callback?: Callback&lt;GravityResponse&gt;): void

取消订阅重力传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                | 必填 | 说明                                                         |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).GRAVITY                      | 是   | 传感器类型，该值固定为SensorId.GRAVITY。                     |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.GRAVITY, callback1);
  sensor.on(sensor.SensorId.GRAVITY, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.GRAVITY, callback1);
  // 取消注册SensorId.GRAVITY的所有回调
  sensor.off(sensor.SensorId.GRAVITY);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}

```

## sensor.off(GRAVITY)<sup>19+</sup>

off(type: SensorId.GRAVITY, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;GravityResponse&gt;): void

取消订阅重力传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offGravityChange](#sensoroffgravitychange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                | 必填 | 说明                                                         |
|------------------| --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).GRAVITY                      | 是   | 传感器类型，该值固定为SensorId.GRAVITY。                     |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[GravityResponse](#gravityresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.GravityResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.GRAVITY;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offGravityChange<sup>23+</sup>

offGravityChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;GravityResponse&gt;): void

取消订阅重力传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(GRAVITY)](#sensoroffgravity19)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                | 必填 | 说明                                                         |
|------------------| --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[GravityResponse](#gravityresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.GravityResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onGravityChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onGravityChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offGravityChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offGravityChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(GYROSCOPE)<sup>9+</sup> 

off(type: SensorId.GYROSCOPE, callback?: Callback&lt;GyroscopeResponse&gt;): void

取消订阅陀螺仪传感器数据。

**需要权限**：ohos.permission.GYROSCOPE

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).GYROSCOPE                        | 是   | 传感器类型，该值固定为SensorId.GYROSCOPE。                   |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.GYROSCOPE, callback1);
  sensor.on(sensor.SensorId.GYROSCOPE, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.GYROSCOPE, callback1);
  // 取消注册SensorId.GYROSCOPE的所有回调
  sensor.off(sensor.SensorId.GYROSCOPE);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(GYROSCOPE)<sup>19+</sup>

off(type: SensorId.GYROSCOPE, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;GyroscopeResponse&gt;): void

取消订阅陀螺仪传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offGyroscopeChange](#sensoroffgyroscopechange23)

**需要权限**：ohos.permission.GYROSCOPE

**原子化服务API**：从API Version 19开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                    | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).GYROSCOPE                        | 是   | 传感器类型，该值固定为SensorId.GYROSCOPE。                   |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.GyroscopeResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.GYROSCOPE;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offGyroscopeChange<sup>23+</sup>

offGyroscopeChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;GyroscopeResponse&gt;): void

取消订阅陀螺仪传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(GYROSCOPE)](#sensoroffgyroscope19)

**需要权限**：ohos.permission.GYROSCOPE

**原子化服务API**：从API Version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                    | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.GyroscopeResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onGyroscopeChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onGyroscopeChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offGyroscopeChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offGyroscopeChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(GYROSCOPE_UNCALIBRATED)<sup>9+</sup> 

off(type: SensorId.GYROSCOPE_UNCALIBRATED, callback?: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

 取消订阅未校准陀螺仪传感器数据。

**需要权限**：ohos.permission.GYROSCOPE

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).GYROSCOPE_UNCALIBRATED                | 是   | 传感器类型，该值固定为SensorId.GYROSCOPE_UNCALIBRATED。      |
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.GYROSCOPE_UNCALIBRATED, callback1);
  sensor.on(sensor.SensorId.GYROSCOPE_UNCALIBRATED, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.GYROSCOPE_UNCALIBRATED, callback1);
  // 取消注册SensorId.GYROSCOPE_UNCALIBRATED的所有回调
  sensor.off(sensor.SensorId.GYROSCOPE_UNCALIBRATED);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(GYROSCOPE_UNCALIBRATED)<sup>19+</sup>

off(type: SensorId.GYROSCOPE_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

取消订阅未校准陀螺仪传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offGyroscopeUncalibratedChange](#sensoroffgyroscopeuncalibratedchange23)

**需要权限**：ohos.permission.GYROSCOPE

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).GYROSCOPE_UNCALIBRATED                | 是   | 传感器类型，该值固定为SensorId.GYROSCOPE_UNCALIBRATED。      |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.GyroscopeUncalibratedResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.GYROSCOPE_UNCALIBRATED;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offGyroscopeUncalibratedChange<sup>23+</sup>

offGyroscopeUncalibratedChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

取消订阅未校准陀螺仪传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(GYROSCOPE_UNCALIBRATED)](#sensoroffgyroscope_uncalibrated19)

**需要权限**：ohos.permission.GYROSCOPE

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.GyroscopeUncalibratedResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onGyroscopeUncalibratedChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onGyroscopeUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offGyroscopeUncalibratedChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offGyroscopeUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(HALL)<sup>9+</sup> 

off(type: SensorId.HALL, callback?: Callback&lt;HallResponse&gt;): void

取消订阅霍尔传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                          | 必填 | 说明                                                         |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).HALL                   | 是   | 传感器类型，该值固定为SensorId.HALL。                        |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.HALL, callback1);
  sensor.on(sensor.SensorId.HALL, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.HALL, callback1);
  // 取消注册SensorId.HALL的所有回调
  sensor.off(sensor.SensorId.HALL);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(HALL)<sup>19+</sup>

off(type: SensorId.HALL, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;HallResponse&gt;): void

取消订阅霍尔传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offHallChange](#sensoroffhallchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                          | 必填 | 说明                                                         |
|------------------| --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).HALL                   | 是   | 传感器类型，该值固定为SensorId.HALL。                        |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[HallResponse](#hallresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.HallResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.HALL;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offHallChange<sup>23+</sup>

offHallChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;HallResponse&gt;): void

取消订阅霍尔传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(HALL)](#sensoroffhall19)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                          | 必填 | 说明                                                         |
|------------------| --------------------------------------------- | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[HallResponse](#hallresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.HallResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onHallChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onHallChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offHallChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offHallChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(HEART_RATE)<sup>9+</sup> 

off(type: SensorId.HEART_RATE, callback?: Callback&lt;HeartRateResponse&gt;): void

取消订阅心率传感器数据。

**需要权限**：ohos.permission.READ_HEALTH_DATA 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).HEART_RATE                       | 是   | 传感器类型，该值固定为SensorId.HEART_RATE。                  |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.HEART_RATE, callback1);
  sensor.on(sensor.SensorId.HEART_RATE, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.HEART_RATE, callback1);
  // 取消注册SensorId.HEART_RATE的所有回调
  sensor.off(sensor.SensorId.HEART_RATE);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(HEART_RATE)<sup>19+</sup>

off(type: SensorId.HEART_RATE, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;HeartRateResponse&gt;): void

取消订阅心率传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offHeartRateChange](#sensoroffheartratechange23)

**需要权限**：ohos.permission.READ_HEALTH_DATA

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                    | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).HEART_RATE                       | 是   | 传感器类型，该值固定为SensorId.HEART_RATE。                  |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.HeartRateResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.HEART_RATE;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offHeartRateChange<sup>23+</sup>

offHeartRateChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;HeartRateResponse&gt;): void

取消订阅心率传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(HEART_RATE)](#sensoroffheart_rate19)

**需要权限**：ohos.permission.READ_HEALTH_DATA

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                    | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.HeartRateResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onHeartRateChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onHeartRateChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offHeartRateChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offHeartRateChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(HUMIDITY)<sup>9+</sup> 

off(type: SensorId.HUMIDITY, callback?: Callback&lt;HumidityResponse&gt;): void

取消订阅湿度传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                  | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).HUMIDITY                       | 是   | 传感器类型，该值固定为SensorId.HUMIDITY。                    |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.HUMIDITY, callback1);
  sensor.on(sensor.SensorId.HUMIDITY, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.HUMIDITY, callback1);
  // 取消注册SensorId.HUMIDITY的所有回调
  sensor.off(sensor.SensorId.HUMIDITY);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(HUMIDITY)<sup>19+</sup>

off(type: SensorId.HUMIDITY, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;HumidityResponse&gt;): void

取消订阅湿度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offHumidityChange](#sensoroffhumiditychange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                  | 必填 | 说明                                                         |
|------------------| ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).HUMIDITY                       | 是   | 传感器类型，该值固定为SensorId.HUMIDITY。                    |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[HumidityResponse](#humidityresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.HumidityResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.HUMIDITY;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offHumidityChange<sup>23+</sup>

offHumidityChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;HumidityResponse&gt;): void

取消订阅湿度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(HUMIDITY)](#sensoroffhumidity19)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                  | 必填 | 说明                                                         |
|------------------| ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[HumidityResponse](#humidityresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.HumidityResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onHumidityChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onHumidityChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offHumidityChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offHumidityChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(LINEAR_ACCELEROMETER)<sup>9+</sup> 

off(type: SensorId.LINEAR_ACCELEROMETER, callback?: Callback&lt;LinearAccelerometerResponse&gt;): void

取消订阅线性加速度传感器数据。

**需要权限**：ohos.permission.ACCELEROMETER 

**系统能力**：SystemCapability.Sensors.Sensor 

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).LINEAR_ACCELEROMETER                  | 是   | 传感器类型，该值固定为SensorId.LINEAR_ACCELERATION。         |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.LINEAR_ACCELEROMETER, callback1);
  sensor.on(sensor.SensorId.LINEAR_ACCELEROMETER, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.LINEAR_ACCELEROMETER, callback1);
  // 取消注册SensorId.LINEAR_ACCELEROMETER的所有回调
  sensor.off(sensor.SensorId.LINEAR_ACCELEROMETER);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(LINEAR_ACCELEROMETER)<sup>19+</sup>

off(type: SensorId.LINEAR_ACCELEROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;LinearAccelerometerResponse&gt;): void

取消订阅线性加速度传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offLinearAccelerometerChange](#sensorofflinearaccelerometerchange23)

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).LINEAR_ACCELEROMETER                  | 是   | 传感器类型，该值固定为SensorId.LINEAR_ACCELERATION。         |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.LinearAccelerometerResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.LINEAR_ACCELEROMETER;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offLinearAccelerometerChange<sup>23+</sup>

offLinearAccelerometerChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;LinearAccelerometerResponse&gt;): void

取消订阅线性加速度传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(LINEAR_ACCELEROMETER)](#sensorofflinear_accelerometer19)

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.LinearAccelerometerResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onLinearAccelerometerChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onLinearAccelerometerChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offLinearAccelerometerChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offLinearAccelerometerChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(MAGNETIC_FIELD)<sup>9+</sup> 

off(type: SensorId.MAGNETIC_FIELD, callback?: Callback&lt;MagneticFieldResponse&gt;): void

取消订阅磁场传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor 

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD                        | 是   | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD。              |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.MAGNETIC_FIELD, callback1);
  sensor.on(sensor.SensorId.MAGNETIC_FIELD, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.MAGNETIC_FIELD, callback1);
  // 取消注册SensorId.MAGNETIC_FIELD的所有回调
  sensor.off(sensor.SensorId.MAGNETIC_FIELD);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(MAGNETIC_FIELD)<sup>19+</sup>

off(type: SensorId.MAGNETIC_FIELD, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;MagneticFieldResponse&gt;): void

取消订阅磁场传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offMagneticFieldChange](#sensoroffmagneticfieldchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).MAGNETIC_FIELD                        | 是   | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD。              |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.MagneticFieldResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.MAGNETIC_FIELD;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offMagneticFieldChange<sup>23+</sup>

offMagneticFieldChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;MagneticFieldResponse&gt;): void

取消订阅磁场传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(MAGNETIC_FIELD)](#sensoroffmagnetic_field19)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.MagneticFieldResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onMagneticFieldChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onMagneticFieldChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offMagneticFieldChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offMagneticFieldChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(MAGNETIC_FIELD_UNCALIBRATED)<sup>9+</sup> 

off(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback?: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

取消订阅未校准的磁场传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor 

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD_UNCALIBRATED           | 是   | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback1);
  sensor.on(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback1);
  // 取消注册SensorId.MAGNETIC_FIELD_UNCALIBRATED的所有回调
  sensor.off(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(MAGNETIC_FIELD_UNCALIBRATED)<sup>19+</sup>

off(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

取消订阅未校准的磁场传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offMagneticFieldUncalibratedChange](#sensoroffmagneticfielduncalibratedchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).MAGNETIC_FIELD_UNCALIBRATED           | 是   | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD_UNCALIBRATED。 |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.MagneticFieldUncalibratedResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offMagneticFieldUncalibratedChange<sup>23+</sup>

offMagneticFieldUncalibratedChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

取消订阅未校准的磁场传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(MAGNETIC_FIELD_UNCALIBRATED)](#sensoroffmagnetic_field_uncalibrated19)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.MagneticFieldUncalibratedResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onMagneticFieldUncalibratedChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onMagneticFieldUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offMagneticFieldUncalibratedChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offMagneticFieldUncalibratedChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(ORIENTATION)<sup>9+</sup> 

off(type: SensorId.ORIENTATION, callback?: Callback&lt;OrientationResponse&gt;): void

取消订阅方向传感器数据。

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ORIENTATION                          | 是   | 传感器类型，该值固定为SensorId.ORIENTATION。                 |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.ORIENTATION, callback1);
  sensor.on(sensor.SensorId.ORIENTATION, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.ORIENTATION, callback1);
  // 取消注册SensorId.ORIENTATION的所有回调
  sensor.off(sensor.SensorId.ORIENTATION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(ORIENTATION)<sup>19+</sup>

off(type: SensorId.ORIENTATION, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;OrientationResponse&gt;): void

取消订阅方向传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offOrientationChange](#sensorofforientationchange23)

**原子化服务API**：从API Version 19开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ORIENTATION                          | 是   | 传感器类型，该值固定为SensorId.ORIENTATION。                 |
| sensorInfoParam | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.OrientationResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.ORIENTATION;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offOrientationChange<sup>23+</sup>

offOrientationChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;OrientationResponse&gt;): void

取消订阅方向传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(ORIENTATION)](#sensorofforientation19)

**原子化服务API**：从API Version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| sensorInfoParam | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.OrientationResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onOrientationChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onOrientationChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offOrientationChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offOrientationChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(PEDOMETER)<sup>9+</sup>

off(type: SensorId.PEDOMETER, callback?: Callback&lt;PedometerResponse&gt;): void

取消订阅计步器传感器数据。

**需要权限**：ohos.permission.ACTIVITY_MOTION 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PEDOMETER                        | 是   | 传感器类型，该值固定为SensorId.PEDOMETER。                   |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.PEDOMETER, callback1);
  sensor.on(sensor.SensorId.PEDOMETER, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.PEDOMETER, callback1);
  // 取消注册SensorId.ORIENTATION的所有回调
  sensor.off(sensor.SensorId.PEDOMETER);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(PEDOMETER)<sup>19+</sup>

off(type: SensorId.PEDOMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;PedometerResponse&gt;): void

取消订阅计步器传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offPedometerChange](#sensoroffpedometerchange23)

**需要权限**：ohos.permission.ACTIVITY_MOTION

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                    | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).PEDOMETER                        | 是   | 传感器类型，该值固定为SensorId.PEDOMETER。                   |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[PedometerResponse](#pedometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.PedometerResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.PEDOMETER;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offPedometerChange<sup>23+</sup>

offPedometerChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;PedometerResponse&gt;): void

取消订阅计步器传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(PEDOMETER)](#sensoroffpedometer19)

**需要权限**：ohos.permission.ACTIVITY_MOTION

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                    | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[PedometerResponse](#pedometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.PedometerResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onPedometerChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onPedometerChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offPedometerChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offPedometerChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(PEDOMETER_DETECTION)<sup>9+</sup> 

off(type: SensorId.PEDOMETER_DETECTION, callback?: Callback&lt;PedometerDetectionResponse&gt;): void

取消订阅计步检测器传感器数据。

**需要权限**：ohos.permission.ACTIVITY_MOTION 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PEDOMETER_DETECTION                   | 是   | 传感器类型，该值固定为SensorId.PEDOMETER_DETECTION。         |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.PEDOMETER_DETECTION, callback1);
  sensor.on(sensor.SensorId.PEDOMETER_DETECTION, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.PEDOMETER_DETECTION, callback1);
  // 取消注册SensorId.PEDOMETER_DETECTION的所有回调
  sensor.off(sensor.SensorId.PEDOMETER_DETECTION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(PEDOMETER_DETECTION)<sup>19+</sup>

off(type: SensorId.PEDOMETER_DETECTION, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;PedometerDetectionResponse&gt;): void

取消订阅计步检测器传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offPedometerDetectionChange](#sensoroffpedometerdetectionchange23)

**需要权限**：ohos.permission.ACTIVITY_MOTION

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).PEDOMETER_DETECTION                   | 是   | 传感器类型，该值固定为SensorId.PEDOMETER_DETECTION。         |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.PedometerDetectionResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.PEDOMETER_DETECTION;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offPedometerDetectionChange<sup>23+</sup>

offPedometerDetectionChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;PedometerDetectionResponse&gt;): void

取消订阅计步检测器传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(PEDOMETER_DETECTION)](#sensoroffpedometer_detection19)

**需要权限**：ohos.permission.ACTIVITY_MOTION

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.PedometerDetectionResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onPedometerDetectionChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onPedometerDetectionChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offPedometerDetectionChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offPedometerDetectionChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(PROXIMITY)<sup>9+</sup>  

off(type: SensorId.PROXIMITY, callback?: Callback&lt;ProximityResponse&gt;): void

取消订阅接近光传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PROXIMITY                        | 是   | 传感器类型，该值固定为SensorId.PROXIMITY。                   |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.PROXIMITY, callback1);
  sensor.on(sensor.SensorId.PROXIMITY, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.PROXIMITY, callback1);
  // 取消注册SensorId.PROXIMITY的所有回调
  sensor.off(sensor.SensorId.PROXIMITY);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(PROXIMITY)<sup>19+</sup>

off(type: SensorId.PROXIMITY, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;ProximityResponse&gt;): void

取消订阅接近光传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offProximityChange](#sensoroffproximitychange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名             | 类型                                                    | 必填 | 说明                                                         |
|-----------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type            | [SensorId](#sensorid9).PROXIMITY                        | 是   | 传感器类型，该值固定为SensorId.PROXIMITY。                   |
| sensorInfoParam | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback        | Callback&lt;[ProximityResponse](#proximityresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.ProximityResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.PROXIMITY;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offProximityChange<sup>23+</sup>

offProximityChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;ProximityResponse&gt;): void

取消订阅接近光传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(PROXIMITY)](#sensoroffproximity19)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名             | 类型                                                    | 必填 | 说明                                                         |
|-----------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| sensorInfoParam | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback        | Callback&lt;[ProximityResponse](#proximityresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.ProximityResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onProximityChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onProximityChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offProximityChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offProximityChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(ROTATION_VECTOR)<sup>9+</sup> 

off(type: SensorId.ROTATION_VECTOR, callback?: Callback&lt;RotationVectorResponse&gt;): void

取消订阅旋转矢量传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ROTATION_VECTOR                       | 是   | 传感器类型，该值固定为SensorId.ROTATION_VECTOR。             |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.ROTATION_VECTOR, callback1);
  sensor.on(sensor.SensorId.ROTATION_VECTOR, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.ROTATION_VECTOR, callback1);
  // 取消注册SensorId.ROTATION_VECTOR的所有回调
  sensor.off(sensor.SensorId.ROTATION_VECTOR);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(ROTATION_VECTOR)<sup>19+</sup>

off(type: SensorId.ROTATION_VECTOR, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;RotationVectorResponse&gt;): void

取消订阅旋转矢量传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offRotationVectorChange](#sensoroffrotationvectorchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).ROTATION_VECTOR                       | 是   | 传感器类型，该值固定为SensorId.ROTATION_VECTOR。             |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.RotationVectorResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.ROTATION_VECTOR;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offRotationVectorChange<sup>23+</sup>

offRotationVectorChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;RotationVectorResponse&gt;): void

取消订阅旋转矢量传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(ROTATION_VECTOR)](#sensoroffrotation_vector19)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.RotationVectorResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onRotationVectorChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onRotationVectorChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offRotationVectorChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offRotationVectorChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(SIGNIFICANT_MOTION)<sup>9+</sup> 

off(type: SensorId.SIGNIFICANT_MOTION, callback?: Callback&lt;SignificantMotionResponse&gt;): void

取消订阅有效运动传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).SIGNIFICANT_MOTION                    | 是   | 传感器类型，该值固定为SensorId.SIGNIFICANT_MOTION。          |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.SIGNIFICANT_MOTION, callback1);
  sensor.on(sensor.SensorId.SIGNIFICANT_MOTION, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.SIGNIFICANT_MOTION, callback1);
  // 取消注册SensorId.SIGNIFICANT_MOTION的所有回调
  sensor.off(sensor.SensorId.SIGNIFICANT_MOTION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(SIGNIFICANT_MOTION)<sup>19+</sup>

off(type: SensorId.SIGNIFICANT_MOTION, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;SignificantMotionResponse&gt;): void

取消订阅有效运动传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offSignificantMotionChange](#sensoroffsignificantmotionchange23)

**系统能力**:SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).SIGNIFICANT_MOTION                    | 是   | 传感器类型，该值固定为SensorId.SIGNIFICANT_MOTION。          |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.SignificantMotionResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.SIGNIFICANT_MOTION;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offSignificantMotionChange<sup>23+</sup>

offSignificantMotionChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;SignificantMotionResponse&gt;): void

取消订阅有效运动传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(SIGNIFICANT_MOTION)](#sensoroffsignificant_motion19)

**系统能力**:SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.SignificantMotionResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onSignificantMotionChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onSignificantMotionChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offSignificantMotionChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offSignificantMotionChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off(WEAR_DETECTION)<sup>9+</sup> 

off(type: SensorId.WEAR_DETECTION, callback?: Callback&lt;WearDetectionResponse&gt;): void

取消订阅佩戴检测传感器数据。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).WEAR_DETECTION                        | 是   | 传感器类型，该值固定为SensorId.WEAR_DETECTION。              |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.WEAR_DETECTION, callback1);
  sensor.on(sensor.SensorId.WEAR_DETECTION, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.WEAR_DETECTION, callback1);
  // 取消注册SensorId.WEAR_DETECTION的所有回调
  sensor.off(sensor.SensorId.WEAR_DETECTION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off(WEAR_DETECTION)<sup>19+</sup>

off(type: SensorId.WEAR_DETECTION, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;WearDetectionResponse&gt;): void

取消订阅佩戴检测传感器数据。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的接口ArkTS-Sta是[offWearDetectionChange](#sensoroffweardetectionchange23)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).WEAR_DETECTION                        | 是   | 传感器类型，该值固定为SensorId.WEAR_DETECTION。              |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.WearDetectionResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.WEAR_DETECTION;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.offWearDetectionChange<sup>23+</sup>

offWearDetectionChange(sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;WearDetectionResponse&gt;): void

取消订阅佩戴检测传感器数据。

**ArkTS模式**：该接口适用于ArkTS-Sta。

**相关接口**：该接口对应的接口ArkTS-Dyn是[off(WEAR_DETECTION)](#sensoroffwear_detection19)

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名              | 类型                                                         | 必填 | 说明                                                         |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  否 | 传感器传入设置参数，可指定deviceId、sensorIndex |
| callback         | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. | 

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.WearDetectionResponse) => {
  console.log(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onWearDetectionChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onWearDetectionChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offWearDetectionChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offWearDetectionChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

## sensor.off('sensorStatusChange')<sup>19+<sup>

off(type: 'sensorStatusChange', callback?: Callback&lt;SensorStatusEvent&gt;): void

取消监听传感器变化。

**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**相关接口**：该接口对应的ArkTS-Sta接口是[offSensorStatusChange](#sensoroffsensorstatuschange23)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| sensorStatusChange     |  固定传入'sensorStatusChange'         | 是   | 状态监听固定参数。             |
| callback | Callback&lt;[SensorStatusEvent](#sensorstatusevent19)&gt; | 否   | sensor.on传入的回调函数，不传则取消所有监听。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  const statusChangeCallback = (data: sensor.SensorStatusEvent) => {
    console.info('sensorStatusChange : ' + JSON.stringify(data));
  }
  const statusChangeCallback2 = (data: sensor.SensorStatusEvent) => {
    console.info('sensorStatusChange2 : ' + JSON.stringify(data));
  }
  // 注册两个设备上线消息监听回调
  sensor.on('sensorStatusChange', statusChangeCallback);
  sensor.on('sensorStatusChange', statusChangeCallback2);
  
  // 3秒后注销第一个监听
  setTimeout(() => {
    sensor.off('sensorStatusChange', statusChangeCallback);
  }, 3000);
  // 5秒后注销所有监听
  setTimeout(() => {
    sensor.off('sensorStatusChange');
  }, 5000);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.offSensorStatusChange<sup>23+<sup>

offSensorStatusChange(callback?: Callback&lt;SensorStatusEvent&gt;): void

取消监听传感器变化。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**相关接口**：该接口对应的ArkTS-Dyn接口是[off('sensorStatusChange')](#sensoroffsensorstatuschange19)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[SensorStatusEvent](#sensorstatusevent19)&gt; | 否   | sensor.on传入的回调函数，不传则取消所有监听。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  const statusChangeCallback = (data: sensor.SensorStatusEvent) => {
    console.info('sensorStatusChange : ' + JSON.stringify(data));
  }
  const statusChangeCallback2 = (data: sensor.SensorStatusEvent) => {
    console.info('sensorStatusChange2 : ' + JSON.stringify(data));
  }
  // 注册两个设备上线消息监听回调
  sensor.onSensorStatusChange(statusChangeCallback);
  sensor.onSensorStatusChange(statusChangeCallback2);

  // 3秒后注销第一个监听
  setTimeout(() => {
    sensor.offSensorStatusChange(statusChangeCallback);
  }, 3000);
  // 5秒后注销所有监听
  setTimeout(() => {
    sensor.offSensorStatusChange();
  }, 5000);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getSensorListByDeviceSync<sup>19+</sup> 

ArkTS-Dyn: getSensorListByDeviceSync(deviceId?: number): Array&lt;Sensor&gt; 

ArkTS-Sta: getSensorListByDeviceSync(deviceId?: int): Array&lt;Sensor&gt; 

同步获取设备的所有传感器信息。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名          | 类型                                                         | 必填 | 说明     |
| --------------- | ------------------------------------------------------------ | ---- |--------|
| deviceId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否   | 设备ID，默认为查询本地设备。 |

**返回值**：

| 类型                                                       | 说明           |
| ---------------------------------------------------------- | -------------- |
| Array&lt;[Sensor](#sensor9)&gt;           | 传感器属性列表。                  |


**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const deviceId = 1;
  // 第一个参数deviceId 非必填
  const sensorList: sensor.Sensor[] = sensor.getSensorListByDeviceSync(deviceId);
  console.log(`sensorList length: ${sensorList.length}`);
  console.log(`sensorList: ${JSON.stringify(sensorList)}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get sensorList. Code: ${e.code}, message: ${e.message}`);
}
```


## sensor.getSingleSensorByDeviceSync<sup>19+</sup> 

ArkTS-Dyn: getSingleSensorByDeviceSync(type: SensorId, deviceId?: number): Array&lt;Sensor&gt;

ArkTS-Sta: getSingleSensorByDeviceSync(type: SensorId, deviceId?: int): Array&lt;Sensor&gt;

同步获取指定设备和类型的传感器信息。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名          | 类型                                                         | 必填 | 说明       |
| --------------- | ------------------------------------------------------------ | ---- |----------|
| type     | [SensorId](#sensorid9) | 是   | 指定传感器类型。 |
| deviceId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否   | 设备ID，默认为查询本地设备。   |


**返回值**：

| 类型                                                       | 说明           |
| ---------------------------------------------------------- | -------------- |
| Array&lt;[Sensor](#sensor9)&gt;           | 传感器属性列表。                  |


**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const deviceId = 1;
  // 第二个参数deviceId 非必填
  const sensorList: sensor.Sensor[] = sensor.getSingleSensorByDeviceSync(sensor.SensorId.ACCELEROMETER, deviceId);
  console.log(`sensorList length: ${sensorList.length}`);
  console.log(`sensorList Json: ${JSON.stringify(sensorList)}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get sensorList. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getGeomagneticInfo<sup>9+</sup> 

ArkTS-Dyn: getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: number, callback: AsyncCallback&lt;GeomagneticResponse&gt;): void

ArkTS-Sta: getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: long, callback: AsyncCallback&lt;GeomagneticResponse&gt;): void

获取某时刻地球上特定位置的地磁场信息，使用Callback异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名          | 类型                                                         | 必填 | 说明                               |
| --------------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| locationOptions | [LocationOptions](#locationoptions)                          | 是   | 地理位置，包括经度、纬度和海拔高度。                         |
| timeMillis      | ArkTS-Dyn: number <br> ArkTS-Sta: long                                                       | 是   | 获取磁偏角的时间，unix时间戳，单位毫秒。 |
| callback        | AsyncCallback&lt;[GeomagneticResponse](#geomagneticresponse)&gt; | 是   | 回调函数，异步返回地磁场信息。                 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.getGeomagneticInfo({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000,
    (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as sensor.GeomagneticResponse;
      if (error) {
        console.error(`Failed to get geomagneticInfo. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info("Succeeded in getting geomagneticInfo x" + dataValue.x);
      console.info("Succeeded in getting geomagneticInfo y" + dataValue.y);
      console.info("Succeeded in getting geomagneticInfo z" + dataValue.z);
      console.info("Succeeded in getting geomagneticInfo geomagneticDip" + dataValue.geomagneticDip);
      console.info("Succeeded in getting geomagneticInfo deflectionAngle" + dataValue.deflectionAngle);
      console.info("Succeeded in getting geomagneticInfo levelIntensity" + dataValue.levelIntensity);
      console.info("Succeeded in getting geomagneticInfo totalIntensity" + dataValue.totalIntensity);
    });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get geomagneticInfo. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.getGeomagneticInfo({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000,
    (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as sensor.GeomagneticResponse;
      if (error) {
        console.error(`Failed to get geomagneticInfo. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info("Succeeded in getting geomagneticInfo x" + dataValue.x);
      console.info("Succeeded in getting geomagneticInfo y" + dataValue.y);
      console.info("Succeeded in getting geomagneticInfo z" + dataValue.z);
      console.info("Succeeded in getting geomagneticInfo geomagneticDip" + dataValue.geomagneticDip);
      console.info("Succeeded in getting geomagneticInfo deflectionAngle" + dataValue.deflectionAngle);
      console.info("Succeeded in getting geomagneticInfo levelIntensity" + dataValue.levelIntensity);
      console.info("Succeeded in getting geomagneticInfo totalIntensity" + dataValue.totalIntensity);
    });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get geomagneticInfo. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getGeomagneticInfo<sup>9+</sup> 

ArkTS-Dyn: getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: number): Promise&lt;GeomagneticResponse&gt;

ArkTS-Sta: getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: long): Promise&lt;GeomagneticResponse&gt;

获取某时刻地球上特定位置的地磁场信息，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名          | 类型                                | 必填 | 说明                               |
| --------------- | ----------------------------------- | ---- | ---------------------------------- |
| locationOptions | [LocationOptions](#locationoptions) | 是   | 地理位置，包括经度、纬度和海拔高度。                         |
| timeMillis      | ArkTS-Dyn: number <br> ArkTS-Sta: long                              | 是   | 获取磁偏角的时间，unix时间戳，单位毫秒。 |

**返回值**：

| 类型                                                       | 说明           |
| ---------------------------------------------------------- | -------------- |
| Promise&lt;[GeomagneticResponse](#geomagneticresponse)&gt; | Promise对象，使用异步方式返回地磁场信息。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

 ArkTS-Dyn示例：
 
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  const promise = sensor.getGeomagneticInfo({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000);
  promise.then((data: sensor.GeomagneticResponse) => {
    console.info("Succeeded in getting geomagneticInfo x" + data.x);
    console.info("Succeeded in getting geomagneticInfo y" + data.y);
    console.info("Succeeded in getting geomagneticInfo z" + data.z);
    console.info("Succeeded in getting geomagneticInfo geomagneticDip" + data.geomagneticDip);
    console.info("Succeeded in getting geomagneticInfo deflectionAngle" + data.deflectionAngle);
    console.info("Succeeded in getting geomagneticInfo levelIntensity" + data.levelIntensity);
    console.info("Succeeded in getting geomagneticInfo totalIntensity" + data.totalIntensity);
  }, (err: Error) => {
    console.error(`Failed to get geomagneticInfo. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get geomagneticInfo. Code: ${e.code}, message: ${e.message}`);
}
```
  
ArkTS-Sta示例：
  
```ts
 	 import { BusinessError } from '@kit.BasicServicesKit';
 	 import { sensor } from '@kit.SensorServiceKit';
 	 
 	 // 使用try catch对可能出现的异常进行捕获
 	 try {
 	   const promise = sensor.getGeomagneticInfo({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000);
 	   promise.then((data: sensor.GeomagneticResponse) => {
 	     console.info("Succeeded in getting geomagneticInfo x" + data.x);
 	     console.info("Succeeded in getting geomagneticInfo y" + data.y);
 	     console.info("Succeeded in getting geomagneticInfo z" + data.z);
 	     console.info("Succeeded in getting geomagneticInfo geomagneticDip" + data.geomagneticDip);
 	     console.info("Succeeded in getting geomagneticInfo deflectionAngle" + data.deflectionAngle);
 	     console.info("Succeeded in getting geomagneticInfo levelIntensity" + data.levelIntensity);
 	     console.info("Succeeded in getting geomagneticInfo totalIntensity" + data.totalIntensity);
 	   }, (err: Error) => {
 	     console.error(`Failed to get geomagneticInfo. Code: ${err.code}, message: ${err.message}`);
 	   });
 	 } catch (error) {
 	   let e: BusinessError = error as BusinessError;
 	   console.error(`Failed to get geomagneticInfo. Code: ${e.code}, message: ${e.message}`);
 	 }
 ```

## sensor.getDeviceAltitude<sup>9+</sup> 

ArkTS-Dyn: getDeviceAltitude(seaPressure: number, currentPressure: number, callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getDeviceAltitude(seaPressure: double, currentPressure: double, callback: AsyncCallback&lt;double&gt;): void

根据气压值获取海拔高度，使用Callback异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名          | 类型                        | 必填 | 说明                                  |
| --------------- | --------------------------- | ---- | ------------------------------------- |
| seaPressure     | ArkTS-Dyn: number <br> ArkTS-Sta: double                      | 是   | 海平面气压值，单位为hPa。         |
| currentPressure | ArkTS-Dyn: number <br> ArkTS-Sta: double                      | 是   | 指定的气压值，单位为hPa。 |
  
**返回值**：

| 类型                  | 说明                                 |
| --------------------- | ------------------------------------ |
| ArkTS-Dyn: AsyncCallback&lt;number&gt;<br> ArkTS-Sta: AsyncCallback&lt;double&gt; | 回调函数，异步返回指定的气压值对应的海拔高度，单位为米。  |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：
  
```ts
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
  
```ts
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

## sensor.getDeviceAltitude<sup>9+</sup> 

ArkTS-Dyn: getDeviceAltitude(seaPressure: number, currentPressure: number): Promise&lt;number&gt;

ArkTS-Sta: getDeviceAltitude(seaPressure: double, currentPressure: double): Promise&lt;double&gt;

根据气压值获取海拔高度，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名          | 类型   | 必填 | 说明                                  |
| --------------- | ------ | ---- | ------------------------------------- |
| seaPressure     | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 海平面气压值，单位为hPa。         |
| currentPressure | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 指定的气压值，单位为hPa。 |

**返回值**：

| 类型                  | 说明                                 |
| --------------------- | ------------------------------------ |
| ArkTS-Dyn: Promise&lt;number&gt; <br> ArkTS-Sta: Promise&lt;double&gt; | Promise对象，使用异步方式返回指定的气压值对应的海拔高度，单位为米。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let seaPressure = 1013.2;
  let currentPressure = 1500.0;
  const promise = sensor.getDeviceAltitude(seaPressure, currentPressure);
  promise.then((data: number) => {
    console.info('Succeeded in getting sensor_getDeviceAltitude_Promise', data);
  }, (err: Error) => {
    console.error(`Failed to get altitude. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get altitude. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let seaPressure = 1013.2;
  let currentPressure = 1500.0;
  const promise = sensor.getDeviceAltitude(seaPressure, currentPressure);
  promise.then((data: double) => {
    console.info('Succeeded in getting sensor_getDeviceAltitude_Promise', data);
  }, (err: Error) => {
    console.error(`Failed to get altitude. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get altitude. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getInclination<sup>9+</sup> 

ArkTS-Dyn: getInclination(inclinationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getInclination(inclinationMatrix: Array&lt;double&gt;, callback: AsyncCallback&lt;double&gt;): void

根据倾斜矩阵计算地磁倾角，使用Callback异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名            | 类型                        | 必填 | 说明                         |
| ----------------- | --------------------------- | ---- | ---------------------------- |
| inclinationMatrix | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta: Array&lt;double&gt; | 是   | 倾斜矩阵。|
| callback          |ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: AsyncCallback&lt;double&gt; | 是   | 回调函数，异步返回地磁倾角，单位为弧度。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // inclinationMatrix可以为3*3，或者4*4
  let inclinationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ]
  sensor.getInclination(inclinationMatrix, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as number;
    if (error) {
      console.error(`Failed to get inclination. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeeded in getting inclination: ' + dataValue);
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get inclination. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // inclinationMatrix可以为3*3，或者4*4
  let inclinationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ]
  sensor.getInclination(inclinationMatrix, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as double;
    if (error) {
      console.error(`Failed to get inclination. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeeded in getting inclination: ' + dataValue);
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get inclination. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getInclination<sup>9+</sup> 

 ArkTS-Dyn: getInclination(inclinationMatrix: Array&lt;number&gt;): Promise&lt;number&gt;

 ArkTS-Sta: getInclination(inclinationMatrix: Array&lt;double&gt;): Promise&lt;double&gt;

根据倾斜矩阵计算地磁倾角，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名            | 类型                | 必填 | 说明           |
| ----------------- | ------------------- | ---- | -------------- |
| inclinationMatrix | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta: Array&lt;double&gt; | 是   | 倾斜矩阵。 |

**返回值**：

| 类型                  | 说明                         |
| --------------------- | ---------------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;double&gt;  | Promise对象，使用异步方式返回地磁倾斜角，单位为弧度。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // inclinationMatrix可以为3*3，或者4*4
  let inclinationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ]
  const promise = sensor.getInclination(inclinationMatrix);
  promise.then((data: number) => {
    console.info('Succeeded in getting inclination: ' + data);
  }, (err: Error) => {
    console.error(`Failed to get inclination. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get inclination. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // inclinationMatrix可以为3*3，或者4*4
  let inclinationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ]
  const promise = sensor.getInclination(inclinationMatrix);
  promise.then((data: double) => {
    console.info('Succeeded in getting inclination: ' + data);
  }, (err: Error) => {
    console.error(`Failed to get inclination. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get inclination. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getAngleVariation<sup>9+</sup>
 
ArkTS-Dyn: getAngleVariation(currentRotationMatrix: Array&lt;number&gt;, preRotationMatrix: Array&lt;number&gt;,
        callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

ArkTS-Sta: getAngleVariation(currentRotationMatrix: Array&lt;double&gt;, preRotationMatrix: Array&lt;double&gt;,
        callback: AsyncCallback&lt;Array&lt;double&gt;&gt;): void

计算两个旋转矩阵之间的角度变化，使用Callback异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名                | 类型                                     | 必填 | 说明                              |
| --------------------- | ---------------------------------------- | ---- | --------------------------------- |
| currentRotationMatrix | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta: Array&lt;double&gt;                      | 是   | 当前旋转矩阵。                |
| preRotationMatrix     | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta:  Array&lt;double&gt;                      | 是   | 相对旋转矩阵。                    |
| callback              | ArkTS-Dyn: AsyncCallback&lt;Array&lt;number&gt;&gt;<br> ArkTS-Sta: AsyncCallback&lt;Array&lt;double&gt;&gt; | 是   | 回调函数，异步返回绕z、x、y轴方向的旋转角度。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 旋转矩阵可以为3*3，或者4*4
  let currentRotationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ];
  let preRotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  sensor.getAngleVariation(currentRotationMatrix, preRotationMatrix, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as Array<number>;
    if (error) {
      console.error(`Failed to get angle variation. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    if (dataValue.length < 3) {
      console.error("Failed to get angle variation, length" + dataValue.length);
    }
    console.info("Z: " + dataValue[0]);
    console.info("X: " + dataValue[1]);
    console.info("Y  : " + dataValue[2]);
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get angle variation. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 旋转矩阵可以为3*3，或者4*4
  let currentRotationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ];
  let preRotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  sensor.getAngleVariation(currentRotationMatrix, preRotationMatrix, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as Array<double>;
    if (error) {
      console.error(`Failed to get angle variation. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    if (dataValue.length < 3) {
      console.error("Failed to get angle variation, length" + dataValue.length);
    }
    console.info("Z: " + dataValue[0]);
    console.info("X: " + dataValue[1]);
    console.info("Y  : " + dataValue[2]);
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get angle variation. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getAngleVariation<sup>9+</sup>

ArkTS-Dyn: getAngleVariation(currentRotationMatrix: Array&lt;number&gt;, preRotationMatrix: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt; 

ArkTS-Sta: getAngleVariation(currentRotationMatrix: Array&lt;double&gt;, preRotationMatrix: Array&lt;double&gt;): Promise&lt;Array&lt;double&gt;&gt; 

得到两个旋转矩阵之间的角度变化，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名                | 类型                | 必填 | 说明               |
| --------------------- | ------------------- | ---- | ------------------ |
| currentRotationMatrix | ArkTS-Dyn: Array&lt;number&gt; <br> ArkTS-Sta: Array&lt;double&gt; | 是   | 当前旋转矩阵。 |
| preRotationMatrix     | ArkTS-Dyn: Array&lt;number&gt; <br> ArkTS-Sta: Array&lt;double&gt; | 是   | 相对旋转矩阵。                  |

**返回值**：

| 类型                               | 说明                              |
| ---------------------------------- | --------------------------------- |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt; <br> ArkTS-Sta: Promise&lt;Array&lt;double&gt;&gt;   | Promise对象，使用异步方式返回绕z、x、y轴方向的旋转角度。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 旋转矩阵可以为3*3，或者4*4
  let currentRotationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ];
  let preRotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  const promise = sensor.getAngleVariation(currentRotationMatrix, preRotationMatrix);
  promise.then((data: Array<number>) => {
    if (data.length < 3) {
      console.error("Failed to get angle variation, length" + data.length);
    }
    console.info("Z: " + data[0]);
    console.info("X: " + data[1]);
    console.info("Y  : " + data[2]);
  }, (err: Error) => {
    console.error(`Failed to get angle variation. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get angle variation. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 旋转矩阵可以为3*3，或者4*4
  let currentRotationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ];
  let preRotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  const promise = sensor.getAngleVariation(currentRotationMatrix, preRotationMatrix);
  promise.then((data: Array<double>) => {
    if (data.length < 3) {
      console.error("Failed to get angle variation, length" + data.length);
    }
    console.info("Z: " + data[0]);
    console.info("X: " + data[1]);
    console.info("Y  : " + data[2]);
  }, (err: Error) => {
    console.error(`Failed to get angle variation. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get angle variation. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getRotationMatrix<sup>9+</sup> 

ArkTS-Dyn: getRotationMatrix(rotationVector: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

ArkTS-Sta: getRotationMatrix(rotationVector: Array&lt;double&gt;, callback: AsyncCallback&lt;Array&lt;double&gt;&gt;): void

根据旋转矢量获取旋转矩阵，使用Callback异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名         | 类型                                     | 必填 | 说明           |
| -------------- | ---------------------------------------- | ---- | -------------- |
| rotationVector | ArkTS-Dyn: Array&lt;number&gt;<br> ArkTS-Sta: Array&lt;double&gt;                      | 是   | 旋转矢量。 |
| callback       | ArkTS-Dyn: AsyncCallback&lt;Array&lt;number&gt;&gt;<br> ArkTS-Sta: AsyncCallback&lt;Array&lt;double&gt;&gt; | 是   | 回调函数，异步返回3*3旋转矩阵。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  sensor.getRotationMatrix(rotationVector, (err: BusinessError, data: Array<number>) => {
    if (err) {
      console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  sensor.getRotationMatrix(rotationVector, (err: BusinessError<void> | null, data: Array<double> | undefined) => {
    if (err) {
      console.error(`Failed to get rotationMatrix. Code: ${err?.code}, message: ${err?.message}`);
      return;
    }
    console.info('Succeeded getting rotationMatrix: ' + JSON.stringify(data));
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getRotationMatrix<sup>9+</sup>

ArkTS-Dyn: getRotationMatrix(rotationVector: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

ArkTS-Sta: getRotationMatrix(rotationVector: Array&lt;double&gt;): Promise&lt;Array&lt;double&gt;&gt;

根据旋转矢量获取旋转矩阵，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名         | 类型                | 必填 | 说明           |
| -------------- | ------------------- | ---- | -------------- |
| rotationVector | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta: Array&lt;double&gt; | 是   | 旋转矢量。 |

**返回值**：

| 类型                               | 说明           |
| ---------------------------------- | -------------- |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt;<br>ArkTS-Sta: Promise&lt;Array&lt;double&gt;&gt; | Promise对象，使用异步方式返回旋转矩阵。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  const promise = sensor.getRotationMatrix(rotationVector);
  promise.then((data: Array<number>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  }, (err: BusinessError) => {
    console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  const promise = sensor.getRotationMatrix(rotationVector);
  promise.then((data) => {
    console.info('Succeeded getting rotationMatrix: ' + JSON.stringify(data));
  }, (err) => {
    console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.transformRotationMatrix<sup>9+</sup> 

ArkTS-Dyn: transformRotationMatrix(inRotationVector: Array&lt;number&gt;, coordinates: CoordinatesOptions,
        callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

ArkTS-Sta: transformRotationMatrix(inRotationVector: Array&lt;double&gt;, coordinates: CoordinatesOptions,
        callback: AsyncCallback&lt;Array&lt;double&gt;&gt;): void

根据指定坐标系映射旋转矩阵，使用Callback异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名           | 类型                                      | 必填 | 说明                   |
| ---------------- | ----------------------------------------- | ---- | ---------------------- |
| inRotationVector | ArkTS-Dyn: Array&lt;number&gt;<br> ArkTS-Sta: Array&lt;double&gt;  | 是   | 旋转矩阵。         |
| coordinates      | [CoordinatesOptions](#coordinatesoptions) | 是   | 指定坐标系方向。       |
| callback         | ArkTS-Dyn: AsyncCallback&lt;Array&lt;number&gt;&gt; <br> ArkTS-Sta: AsyncCallback&lt;Array&lt;double&gt;&gt;  | 是   | 回调函数，异步返回映射后的旋转矩阵。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  sensor.transformRotationMatrix(rotationMatrix, { x: 1, y: 3 }, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as Array<number>;
    if (error) {
      console.error(`Failed to transform rotationMatrix. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    for (let i = 0; i < dataValue.length; i++) {
      console.info('Succeeded in getting data[' + i + '] = ' + dataValue[i]);
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to transform rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：
                                      
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  sensor.transformRotationMatrix(rotationMatrix, { x: 1, y: 3 }, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as Array<double>;
    if (error) {
      console.error(`Failed to transform rotationMatrix. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    for (let i = 0; i < dataValue.length; i++) {
      console.info('Succeeded in getting data[' + i + '] = ' + dataValue[i]);
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to transform rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.transformRotationMatrix<sup>9+</sup>

ArkTS-Dyn: transformRotationMatrix(inRotationVector: Array&lt;number&gt;, coordinates: CoordinatesOptions): Promise&lt;Array&lt;number&gt;&gt;

ArkTS-Sta: transformRotationMatrix(inRotationVector: Array&lt;double&gt;, coordinates: CoordinatesOptions): Promise&lt;Array&lt;double&gt;&gt;

根据指定坐标系映射旋转矩阵，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名           | 类型                                      | 必填 | 说明             |
| ---------------- | ----------------------------------------- | ---- | ---------------- |
| inRotationVector | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta: Array&lt;double&gt;              | 是   | 旋转矩阵。   |
| coordinates      | [CoordinatesOptions](#coordinatesoptions) | 是   | 指定坐标系方向。 |

**返回值**：

| 类型                               | 说明                   |
| ---------------------------------- | ---------------------- |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt;<br>ArkTS-Sta: Promise&lt;Array&lt;double&gt;&gt;  | Promise对象，使用异步方式返回转换后的旋转矩阵。 |
  
**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例** ：

ArkTS-Dyn示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  const promise = sensor.transformRotationMatrix(rotationMatrix, { x: 1, y: 3 });
  promise.then((data: Array<number>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  }, (err: Error) => {
    console.error(`Failed to transform rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to transform rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  const promise = sensor.transformRotationMatrix(rotationMatrix, { x: 1, y: 3 });
  promise.then((data: Array<double>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  }, (err: Error) => {
    console.error(`Failed to transform rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to transform rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getQuaternion<sup>9+</sup> 

ArkTS-Dyn: getQuaternion(rotationVector: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

ArkTS-Sta: getQuaternion(rotationVector: Array&lt;double&gt;, callback: AsyncCallback&lt;Array&lt;double&gt;&gt;): void

根据旋转向量计算归一化四元数，使用Callback异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名         | 类型                                     | 必填 | 说明           |
| -------------- | ---------------------------------------- | ---- | -------------- |
| rotationVector | ArkTS-Dyn: Array&lt;number&gt; <br> ArkTS-Sta: Array&lt;double&gt; | 是   | 旋转矢量。 |
| callback       | ArkTS-Dyn: AsyncCallback&lt;Array&lt;number&gt;&gt; <br> ArkTS-Sta: AsyncCallback&lt;Array&lt;double&gt;&gt; | 是   | 回调函数，异步返回归一化四元数。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  sensor.getQuaternion(rotationVector, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as Array<number>;
    if (error) {
      console.error(`Failed to get quaternion. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    for (let i = 0; i < dataValue.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + dataValue[i]);
    }
  })
} catch (error: Error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get quaternion. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：
                                         
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  sensor.getQuaternion(rotationVector, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as Array<double>;
    if (error) {
      console.error(`Failed to get quaternion. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    for (let i = 0; i < dataValue.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + dataValue[i]);
    }
  })
} catch (error: Error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get quaternion. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getQuaternion<sup>9+</sup>

ArkTS-Dyn: getQuaternion(rotationVector: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

ArkTS-Sta: getQuaternion(rotationVector: Array&lt;double&gt;): Promise&lt;Array&lt;double&gt;&gt;

根据旋转向量计算归一化四元数，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名         | 类型                | 必填 | 说明           |
| -------------- | ------------------- | ---- | -------------- |
| rotationVector | ArkTS-Dyn: Array&lt;number&gt; <br> ArkTS-Sta: Array&lt;double&gt; | 是   | 旋转矢量。 |

**返回值**：
  
| 类型                               | 说明         |
| ---------------------------------- | ------------ |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt;<br>ArkTS-Sta: Promise&lt;Array&lt;double&gt;&gt;| Promise，使用异步方式对象返归一化回四元数。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  const promise = sensor.getQuaternion(rotationVector);
  promise.then((data: Array<number>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  }, (err: Error) => {
    console.error(`Failed to get quaternion. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get quaternion. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  const promise = sensor.getQuaternion(rotationVector);
  promise.then((data: Array<double>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  }, (err: Error) => {
    console.error(`Failed to get quaternion. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get quaternion. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getOrientation<sup>9+</sup>

ArkTS-Dyn: getOrientation(rotationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

ArkTS-Sta: getOrientation(rotationMatrix: Array&lt;double&gt;, callback: AsyncCallback&lt;Array&lt;double&gt;&gt;): void

根据旋转矩阵计算设备方向，使用Callback异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名         | 类型                                     | 必填 | 说明                              |
| -------------- | ---------------------------------------- | ---- | --------------------------------- |
| rotationMatrix | ArkTS-Dyn: Array&lt;number&gt;<br> ArkTS-Sta: Array&lt;double&gt;                      | 是   | 旋转矩阵。                    |
| callback       | ArkTS-Dyn: AsyncCallback&lt;Array&lt;number&gt;&gt;<br> ArkTS-Sta: AsyncCallback&lt;Array&lt;double&gt;&gt; | 是   | 回调函数，异步返回围绕z、x、y轴方向的旋转角度。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let preRotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  sensor.getOrientation(preRotationMatrix, (err: BusinessError, data: Array<number>) => {
    if (err) {
      console.error(`Failed to get orientation. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    if (data.length < 3) {
      console.error("Failed to get orientation, length" + data.length);
    }
    console.info("Succeeded in getting data. Z: " + data[0]);
    console.info("Succeeded in getting data. X: " + data[1]);
    console.info("Succeeded in getting data. Y: " + data[2]);
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get orientation. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let preRotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  sensor.getOrientation(preRotationMatrix, (err: BusinessError<void> | null, data: Array<double> | undefined) => {
    if (err) {
      console.error(`Failed to get orientation. Code: ${err?.code}, message: ${err?.message}`);
      return;
    }
    console.info('Succeeded getting orientation: ' + JSON.stringify(data));
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get orientation. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getOrientation<sup>9+</sup>

ArkTS-Dyn: getOrientation(rotationMatrix: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

ArkTS-Sta: getOrientation(rotationMatrix: Array&lt;double&gt;): Promise&lt;Array&lt;double&gt;&gt;

根据旋转矩阵计算设备的方向，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名         | 类型                | 必填 | 说明           |
| -------------- | ------------------- | ---- | -------------- |
| rotationMatrix | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta: Array&lt;double&gt; | 是   | 旋转矩阵。 |

**返回值**：

| 类型                               | 说明                              |
| ---------------------------------- | --------------------------------- |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt;<br>ArkTS-Sta: Promise&lt;Array&lt;double&gt;&gt; | Promise对象，使用异步方式返回围绕z、x、y轴方向的旋转角度。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let preRotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  const promise = sensor.getOrientation(preRotationMatrix);
  promise.then((data: Array<number>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  }, (err: BusinessError) => {
    console.error(`Failed to getOrientatin. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to getOrientatin Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let preRotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  const promise = sensor.getOrientation(preRotationMatrix);
  promise.then((data) => {
    console.info('Succeeded getting orientation: ' + JSON.stringify(data));
  }, (err) => {
    console.error(`Failed to getOrientatin. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to getOrientatin Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getRotationMatrix<sup>9+</sup> 

ArkTS-Dyn: getRotationMatrix(gravity: Array&lt;number&gt;, geomagnetic: Array&lt;number&gt;, callback: AsyncCallback&lt;RotationMatrixResponse&gt;): void

ArkTS-Sta: getRotationMatrix(gravity: Array&lt;double&gt;, geomagnetic: Array&lt;double&gt;, callback: AsyncCallback&lt;RotationMatrixResponse&gt;): void

根据重力矢量和地磁矢量计算旋转矩阵，使用Callback异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名      | 类型                                                         | 必填 | 说明           |
| ----------- | ------------------------------------------------------------ | ---- | -------------- |
| gravity     | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta: Array&lt;double&gt;                                          | 是   | 重力矢量。 |
| geomagnetic | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta: Array&lt;double&gt;                                          | 是   | 地磁矢量。 |
| callback    | AsyncCallback&lt;[RotationMatrixResponse](#rotationmatrixresponse)&gt; | 是   | 回调函数，异步返回旋转矩阵。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let gravity = [-0.27775216, 0.5351276, 9.788099];
  let geomagnetic = [210.87253, -78.6096, -111.44444];
  sensor.getRotationMatrix(gravity, geomagnetic, (err: BusinessError, data: sensor.RotationMatrixResponse) => {
    if (err) {
      console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting rotationMatrix' + JSON.stringify(data));
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：
  
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let gravity: double[] = [-0.27775216, 0.5351276, 9.788099];
  let geomagnetic: double[] = [210.87253, -78.6096, -111.44444];
  sensor.getRotationMatrix(gravity, geomagnetic, (err: BusinessError<void> | null, data: sensor.RotationMatrixResponse | undefined) => {
    if (err) {
      console.error(`Failed to get rotationMatrix. Code: ${err?.code}, message: ${err?.message}`);
      return;
    }
    console.info('Succeeded in getting rotationMatrix' + JSON.stringify(data));
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getRotationMatrix<sup>9+</sup> 

ArkTS-Dyn: getRotationMatrix(gravity: Array&lt;number&gt;, geomagnetic: Array&lt;number&gt;): Promise&lt;RotationMatrixResponse&gt;

ArkTS-Sta: getRotationMatrix(gravity: Array&lt;double&gt;, geomagnetic: Array&lt;double&gt;): Promise&lt;RotationMatrixResponse&gt;

根据重力矢量和地磁矢量计算旋转矩阵，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名      | 类型                | 必填 | 说明           |
| ----------- | ------------------- | ---- | -------------- |
| gravity     | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta: Array&lt;double&gt; | 是   | 重力向量。 |
| geomagnetic | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta: Array&lt;double&gt; | 是   | 地磁矢量。 |

**返回值**：

| 类型                                                         | 说明           |
| ------------------------------------------------------------ | -------------- |
| Promise&lt;[RotationMatrixResponse](#rotationmatrixresponse)&gt; | Promise对象，使用异步方式返回旋转矩阵。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let gravity = [-0.27775216, 0.5351276, 9.788099];
  let geomagnetic = [210.87253, -78.6096, -111.44444];
  const promise = sensor.getRotationMatrix(gravity, geomagnetic);
  promise.then((data: sensor.RotationMatrixResponse) => {
    console.info('Succeeded in getting rotationMatrix' + JSON.stringify(data));
  }, (err: BusinessError) => {
    console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let gravity = [-0.27775216, 0.5351276, 9.788099];
  let geomagnetic = [210.87253, -78.6096, -111.44444];
  const promise = sensor.getRotationMatrix(gravity, geomagnetic);
  promise.then((data) => {
    console.info('Succeeded in getting rotationMatrix' + JSON.stringify(data));
  }, (err) => {
    console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getSensorList<sup>9+</sup>

getSensorList(callback: AsyncCallback&lt;Array&lt;Sensor&gt;&gt;): void

获取设备上的所有传感器信息，使用Callback异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                           | 必填 | 说明             |
| -------- | ---------------------------------------------- | ---- | ---------------- |
| callback | AsyncCallback&lt;Array&lt;[Sensor](#sensor9)&gt;&gt; | 是   | 回调函数，异步返回传感器属性列表。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.getSensorList((err: BusinessError, data: Array<sensor.Sensor>) => {
    if (err) {
      console.error(`Failed to get sensorList. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + JSON.stringify(data[i]));
    }
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get sensorList. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getSensorList<sup>9+</sup>

 getSensorList(): Promise&lt;Array&lt;Sensor&gt;&gt;

获取设备上的所有传感器信息，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值**：

| 参数名  | 类型                                     | 必填 | 说明             |
| ------- | ---------------------------------------- | ---- | ---------------- |
| promise | Promise&lt;Array&lt;[Sensor](#sensor9)&gt;&gt; | 是   | Promise对象，使用异步方式返回传感器属性列表。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.getSensorList().then((data: Array<sensor.Sensor>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + JSON.stringify(data[i]));
    }
  }, (err: BusinessError) => {
    console.error(`Failed to get sensorList. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get sensorList. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getSensorListSync<sup>12+</sup>

getSensorListSync(): Array&lt;Sensor&gt;

获取设备上的所有传感器信息，使用同步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值**：

| 类型                                    | 必填 | 说明                             |
| --------------------------------------- | ---- | -------------------------------- |
| &lt;Array&lt;[Sensor](#sensor9)&gt;&gt; | 是   | 使用同步方式返回传感器属性列表。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息           |
| -------- | ------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let ret = sensor.getSensorListSync()
  for (let i = 0; i < ret.length; i++) {
    console.info('Succeeded in getting sensor: ' + JSON.stringify(ret[i]));
  }
} catch(error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to get singleSensor . Code: ${e.code}, message: ${e.message}`);
}
```

##  sensor.getSingleSensor<sup>9+</sup>

getSingleSensor(type: SensorId, callback: AsyncCallback&lt;Sensor&gt;): void

获取指定传感器类型的属性信息，使用Callback异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名   | 类型                                    | 必填 | 说明             |
| -------- | --------------------------------------- | ---- | ---------------- |
| type     | [SensorId](#sensorid9)                  | 是   | 指定传感器类型。     |
| callback | AsyncCallback&lt;[Sensor](#sensor9)&gt; | 是   | 回调函数，异步返回指定传感器的属性信息。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |
| 14500102 | The sensor is not supported by the device.                   |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.getSingleSensor(sensor.SensorId.ACCELEROMETER, (err: BusinessError, data: sensor.Sensor) => {
    if (err) {
      console.error(`Failed to get singleSensor. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting sensor: ' + JSON.stringify(data));
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get singleSensor. Code: ${e.code}, message: ${e.message}`);
}
```

##  sensor.getSingleSensor<sup>9+</sup>

 getSingleSensor(type: SensorId): Promise&lt;Sensor&gt;

获取指定类型的传感器信息，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名 | 类型                   | 必填 | 说明         |
| ------ | ---------------------- | ---- | ------------ |
| type   | [SensorId](#sensorid9) | 是   | 传感器类型。 |

**返回值**：

| 参数名  | 类型                              | 必填 | 说明                         |
| ------- | --------------------------------- | ---- | ---------------------------- |
| promise | Promise&lt;[Sensor](#sensor9)&gt; | 是   | 使用异步方式返回传感器信息。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |
| 14500102 | The sensor is not supported by the device.                   |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.getSingleSensor(sensor.SensorId.ACCELEROMETER).then((data: sensor.Sensor) => {
    console.info('Succeeded in getting sensor: ' + JSON.stringify(data));
  }, (err: BusinessError) => {
    console.error(`Failed to get singleSensor . Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get singleSensor . Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getSingleSensorSync<sup>12+</sup>

getSingleSensorSync(type: SensorId): Sensor

获取指定类型的传感器信息，使用同步方式返回结果。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数**：

| 参数名 | 类型                   | 必填 | 说明         |
| ------ | ---------------------- | ---- | ------------ |
| type   | [SensorId](#sensorid9) | 是   | 传感器类型。 |

**返回值**：

| 类型   | 必填 | 说明                         |
| ------ | ---- | ---------------------------- |
| Sensor | 是   | 使用同步方式返回传感器信息。 |

**错误码**：

以下错误码的详细介绍请参见[传感器错误码](errorcode-sensor.md)和[通用错误码](../errorcode-universal.md)。错误码和错误信息会以异常的形式抛出，调用接口时需要使用try catch对可能出现的异常进行捕获操作。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |
| 14500102 | The sensor is not supported by the device.                   |

**示例**：

```ts
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

## SensorId<sup>9+</sup>

表示当前支持订阅或取消订阅的传感器类型。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称                        | 值   | 说明                                                         |
| --------------------------- | ---- | ------------------------------------------------------------ |
| ACCELEROMETER               | 1    | 加速度传感器。<br/>**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。 |
| GYROSCOPE                   | 2    | 陀螺仪传感器。<br/>**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。 |
| AMBIENT_LIGHT               | 5    | 环境光传感器。                                               |
| MAGNETIC_FIELD              | 6    | 磁场传感器。                                                 |
| BAROMETER                   | 8    | 气压计传感器。                                               |
| HALL                        | 10   | 霍尔传感器。                                                 |
| PROXIMITY                   | 12   | 接近光传感器。                                               |
| HUMIDITY                    | 13   | 湿度传感器。                                                 |
| ORIENTATION                 | 256  | 方向传感器。<br/>**原子化服务API**：从API Version 11开始，该接口在支持原子化服务中使用。 |
| GRAVITY                     | 257  | 重力传感器。                                                 |
| LINEAR_ACCELEROMETER        | 258  | 线性加速度传感器。                                           |
| ROTATION_VECTOR             | 259  | 旋转矢量传感器。                                             |
| AMBIENT_TEMPERATURE         | 260  | 环境温度传感器。                                             |
| MAGNETIC_FIELD_UNCALIBRATED | 261  | 未校准磁场传感器。                                           |
| GYROSCOPE_UNCALIBRATED      | 263  | 未校准陀螺仪传感器。                                         |
| SIGNIFICANT_MOTION          | 264  | 有效运动传感器。                                             |
| PEDOMETER_DETECTION         | 265  | 计步检测传感器。                                             |
| PEDOMETER                   | 266  | 计步传感器。                                                 |
| HEART_RATE                  | 278  | 心率传感器。                                                 |
| WEAR_DETECTION              | 280  | 佩戴检测传感器。                                             |
| ACCELEROMETER_UNCALIBRATED  | 281  | 未校准加速度计传感器。                                       |


## SensorInfoParam<sup>19+</sup>

传感器传入设置参数，多传感器情况下通过deviceId、sensorIndex控制指定传感器。

**系统能力**：SystemCapability.Sensors.Sensor

**原子化服务API**：从API Version 19开始，该接口支持在原子化服务中使用。

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23


| 名称          | 类型     | 必填 | 说明                                                                                                                                                     |
|-------------|--------|----|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| deviceId    | ArkTS-Dyn: number <br> ArkTS-Sta: int | 否  | 设备ID：默认值为-1，表示本地设备，其它设备Id需通过[getSensorListByDeviceSync](#sensorgetsensorlistbydevicesync19)查询。<br/>**原子化服务API**：从API Version 19开始，该接口支持在原子化服务中使用。      |
| sensorIndex | ArkTS-Dyn: number <br> ArkTS-Sta: int | 否  | 传感器索引：默认值为0，为设备上的默认传感器，其它传感器Id需通过[getSensorListByDeviceSync](#sensorgetsensorlistbydevicesync19)查询。<br/>**原子化服务API**：从API Version 19开始，该接口支持在原子化服务中使用。 |


## SensorStatusEvent<sup>19+</sup>

设备状态变化事件数据。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

| 名称             | 类型      | 只读 | 可选 | 说明                          |
|----------------|---------|----|----|-----------------------------|
| timestamp      | ArkTS-Dyn: number<br/>ArkTS-Sta: long  | 是  | 否  | 事件发生的时间戳。                   |
| sensorId       | ArkTS-Dyn: number<br/>ArkTS-Sta: int  | 是  | 否  | 传感器ID。                      |
| sensorIndex    | ArkTS-Dyn: number<br/>ArkTS-Sta: int  | 是  | 否  | 传感器索引。                      |
| isSensorOnline | boolean | 是  | 否  | 传感器上线或者下线，true为上线，false为下线。 |
| deviceId       | ArkTS-Dyn: number<br/>ArkTS-Sta: int  | 是  | 否  | 设备ID。                       |
| deviceName     | string  | 是  | 否  | 设备名称。                       |

## SensorType<sup>(deprecated)</sup>

表示要订阅或取消订阅的传感器类型。

**系统能力**：SystemCapability.Sensors.Sensor


| 名称                                       | 值   | 说明                   |
| ------------------------------------------ | ---- | ---------------------- |
| SENSOR_TYPE_ID_ACCELEROMETER               | 1    | 加速度传感器。         |
| SENSOR_TYPE_ID_GYROSCOPE                   | 2    | 陀螺仪传感器。         |
| SENSOR_TYPE_ID_AMBIENT_LIGHT               | 5    | 环境光传感器。         |
| SENSOR_TYPE_ID_MAGNETIC_FIELD              | 6    | 磁场传感器。           |
| SENSOR_TYPE_ID_BAROMETER                   | 8    | 气压计传感器。         |
| SENSOR_TYPE_ID_HALL                        | 10   | 霍尔传感器。           |
| SENSOR_TYPE_ID_PROXIMITY                   | 12   | 接近光传感器。         |
| SENSOR_TYPE_ID_HUMIDITY                    | 13   | 湿度传感器。           |
| SENSOR_TYPE_ID_ORIENTATION                 | 256  | 方向传感器。           |
| SENSOR_TYPE_ID_GRAVITY                     | 257  | 重力传感器。           |
| SENSOR_TYPE_ID_LINEAR_ACCELERATION         | 258  | 线性加速度传感器。     |
| SENSOR_TYPE_ID_ROTATION_VECTOR             | 259  | 旋转矢量传感器。       |
| SENSOR_TYPE_ID_AMBIENT_TEMPERATURE         | 260  | 环境温度传感器。       |
| SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | 261  | 未校准磁场传感器。     |
| SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED      | 263  | 未校准陀螺仪传感器。   |
| SENSOR_TYPE_ID_SIGNIFICANT_MOTION          | 264  | 有效运动传感器。       |
| SENSOR_TYPE_ID_PEDOMETER_DETECTION         | 265  | 计步检测传感器。       |
| SENSOR_TYPE_ID_PEDOMETER                   | 266  | 计步传感器。           |
| SENSOR_TYPE_ID_HEART_RATE                  | 278  | 心率传感器。           |
| SENSOR_TYPE_ID_WEAR_DETECTION              | 280  | 佩戴检测传感器。       |
| SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED  | 281  | 未校准加速度计传感器。 |

## SensorAccuracy<sup>11+</sup>

传感器数据的精度。

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

| 名称    | 值 | 说明                     |
| --------- | ---- | ------------------------ |
| ACCURACY_UNRELIABLE | 0   | 传感器数据不可信。 |
| ACCURACY_LOW | 1   | 传感器低挡位精度。 |
| ACCURACY_MEDIUM | 2   | 传感器中挡位精度。 |
| ACCURACY_HIGH | 3   | 传感器高挡位精度。 |

## Response

传感器数据的时间戳。

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

| 名称      | 类型   | 只读 | 可选 | 说明                     |
| --------- | ------ | ---- | ---- | ------------------------ |
| timestamp | ArkTS-Dyn: number <br> ArkTS-Sta: long | 是   | 是   | 传感器数据上报的时间戳。 |
| accuracy<sup>11+</sup> | [SensorAccuracy](#sensoraccuracy11)<sup>11+</sup> | 是   | 否   | 传感器数据上报的精度挡位值。 |

## Sensor<sup>9+</sup>

指示传感器信息。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称                          | 类型      | 只读 | 可选 | 说明               |
|-----------------------------|---------|----|----|------------------|
| sensorName                  | string  | 是  | 否  | 传感器名称。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23|
| vendorName                  | string  | 是  | 否  | 传感器供应商。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23          |
| firmwareVersion             | string  | 是  | 否  | 传感器固件版本。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23         |
| hardwareVersion             | string  | 是  | 否  | 传感器硬件版本。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23         |
| sensorId                    | ArkTS-Dyn: number <br> ArkTS-Sta: int  | 是  | 否  | 传感器类型id。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23         |
| maxRange                    | ArkTS-Dyn: number <br> ArkTS-Sta: double  | 是  | 否  | 传感器测量范围的最大值。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23     |
| minSamplePeriod             | ArkTS-Dyn: number <br> ArkTS-Sta: long  | 是  | 否  | 允许的最小采样周期。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23       |
| maxSamplePeriod             | ArkTS-Dyn: number <br> ArkTS-Sta: long  | 是  | 否  | 允许的最大采样周期。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23       |
| precision                   | ArkTS-Dyn: number <br> ArkTS-Sta: double  | 是  | 否  | 传感器精度。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23           |
| power                       | ArkTS-Dyn: number <br> ArkTS-Sta: double  | 是  | 否  | 传感器功率的估计值，单位：mA。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23 |
| sensorIndex<sup>19+</sup>   | ArkTS-Dyn: number <br> ArkTS-Sta: int  | 是  | 是  | 传感器索引。<br/>**ArkTS-Dyn起始版本：** 19<br/>**ArkTS-Sta起始版本：** 23           |
| deviceId<sup>19+</sup>      | ArkTS-Dyn: number <br> ArkTS-Sta: int  | 是  | 是  | 设备ID。<br/>**ArkTS-Dyn起始版本：** 19<br/>**ArkTS-Sta起始版本：** 23            |
| deviceName<sup>19+</sup>    | string  | 是  | 是  | 设备名称。<br/>**ArkTS-Dyn起始版本：** 19<br/>**ArkTS-Sta起始版本：** 23            |
| isLocalSensor<sup>19+</sup> | boolean | 是  | 是  | 是否本地传感器。<br/>**ArkTS-Dyn起始版本：** 19<br/>**ArkTS-Sta起始版本：** 23         |
| isMockSensor<sup>23+</sup> | boolean | 是  | 是  | 是否模拟传感器。<br/>**ArkTS-Dyn起始版本：** 23<br/>**ArkTS-Sta起始版本：** 23         |

## AccelerometerResponse

加速度传感器数据，继承于[Response](#response)。

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23


| 名称 | 类型   | 只读 | 可选 | 说明                                                       |
| ---- | ------ | ---- | ---- | ---------------------------------------------------------- |
| x    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备x轴的加速度，单位 : m/s²；取值为实际上报物理量。 |
| y    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备y轴的加速度，单位 : m/s²；取值为实际上报物理量。 |
| z    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备z轴的加速度，单位 : m/s²；取值为实际上报物理量。 |


## LinearAccelerometerResponse

线性加速度传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| x    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备x轴的线性加速度，单位 : m/s²。 |
| y    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备y轴的线性加速度，单位 : m/s²。 |
| z    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备z轴的线性加速度，单位 : m/s²。 |


## AccelerometerUncalibratedResponse

未校准加速度计传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称  | 类型   | 只读 | 可选 | 说明                                           |
| ----- | ------ | ---- | ---- | ---------------------------------------------- |
| x     | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备x轴未校准的加速度，单位 : m/s²。     |
| y     | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备y轴未校准的加速度，单位 : m/s²。     |
| z     | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备z轴未校准的加速度，单位 : m/s²。     |
| biasX | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备x轴未校准的加速度偏量，单位 : m/s²。 |
| biasY | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备y轴未校准的加速度偏量，单位 : m/s²。 |
| biasZ | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备z轴未校准的加速度偏量，单位 : m/s²。 |


## GravityResponse

重力传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| x    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备x轴的重力加速度，单位 : m/s²。 |
| y    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备y轴的重力加速度，单位 : m/s²。 |
| z    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 施加在设备z轴的重力加速度，单位 : m/s²。 |


## OrientationResponse

方向传感器数据，继承于[Response](#response)。

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23


| 名称  | 类型   | 只读 | 可选 | 说明                                                  |
| ----- | ------ | ---- | ---- | ----------------------------------------------------- |
| alpha | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备围绕Z轴的旋转角度，单位：度；取值范围为0-360度。  |
| beta  | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备围绕X轴的旋转角度，单位：度；取值范围为0-±180度。 |
| gamma | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备围绕Y轴的旋转角度，单位：度；取值范围为0-±90度。  |


## RotationVectorResponse

旋转矢量传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称 | 类型   | 只读 | 可选 | 说明              |
| ---- | ------ | ---- | ---- | ----------------- |
| x    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 旋转矢量x轴分量。 |
| y    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 旋转矢量y轴分量。 |
| z    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 旋转矢量z轴分量。 |
| w    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 标量，描述设备相对于某个参考方向的旋转状态，单位：弧度。            |


## GyroscopeResponse

陀螺仪传感器数据，继承于[Response](#response)。

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23


| 名称 | 类型   | 只读 | 可选 | 说明                                                   |
| ---- | ------ | ---- | ---- | ------------------------------------------------------ |
| x    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备x轴的旋转角速度，单位rad/s；取值为实际上报物理量。 |
| y    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备y轴的旋转角速度，单位rad/s；取值为实际上报物理量。 |
| z    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备z轴的旋转角速度，单位rad/s；取值为实际上报物理量。 |


## GyroscopeUncalibratedResponse

未校准陀螺仪传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称  | 类型   | 只读 | 可选 | 说明                                       |
| ----- | ------ | ---- | ---- | ------------------------------------------ |
| x     | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备x轴未校准的旋转角速度，单位rad/s。     |
| y     | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备y轴未校准的旋转角速度，单位rad/s。     |
| z     | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备z轴未校准的旋转角速度，单位rad/s。     |
| biasX | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备x轴未校准的旋转角速度偏量，单位rad/s。 |
| biasY | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备y轴未校准的旋转角速度偏量，单位rad/s。 |
| biasZ | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 设备z轴未校准的旋转角速度偏量，单位rad/s。 |


## SignificantMotionResponse

有效运动传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称   | 类型   | 只读 | 可选 | 说明                                                         |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| scalar | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 表示剧烈运动程度。测量三个物理轴（x、y&nbsp;和&nbsp;z）上，设备是否存在大幅度运动；若存在大幅度运动则数据上报为1。 |


## ProximityResponse

接近光传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称     | 类型   | 只读 | 可选 | 说明                                                       |
| -------- | ------ | ---- | ---- | ---------------------------------------------------------- |
| distance | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 可见物体与设备显示器的接近程度。0表示接近，大于0表示远离。 |


## LightResponse

环境光传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称                            | 类型   | 只读 | 可选 | 说明                                                         |
| ------------------------------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| intensity                       | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 光强（单位：勒克斯）。                                       |
| colorTemperature<sup>12+</sup>  | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 色温（单位：开尔文），可选参数，如果该参数不支持在js层返回未定义，支持则返回正常数值。 |
| infraredLuminance<sup>12+</sup> | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 红外亮度（单位：cd/m²），可选参数，如果该参数不支持在js层返回未定义，支持则返回正常数值。 |


## HallResponse

霍尔传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称   | 类型   | 只读 | 可选 | 说明                                                         |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| status | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 显示霍尔状态。测量设备周围是否存在磁力吸引，0表示没有，大于0表示有。 |


## MagneticFieldResponse

磁场传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称 | 类型   | 只读 | 可选 | 说明                         |
| ---- | ------ | ---- | ---- | ---------------------------- |
| x    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | x轴环境磁场强度，单位 : μT。 |
| y    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | y轴环境磁场强度，单位 : μT。 |
| z    | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | z轴环境磁场强度，单位 : μT。 |


## MagneticFieldUncalibratedResponse

未校准磁场传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称  | 类型   | 只读 | 可选 | 说明                                   |
| ----- | ------ | ---- | ---- | -------------------------------------- |
| x     | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | x轴未校准环境磁场强度，单位 : μT。     |
| y     | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | y轴未校准环境磁场强度，单位 : μT。     |
| z     | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | z轴未校准环境磁场强度，单位 : μT。     |
| biasX | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | x轴未校准环境磁场强度偏量，单位 : μT。 |
| biasY | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | y轴未校准环境磁场强度偏量，单位 : μT。 |
| biasZ | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | z轴未校准环境磁场强度偏量，单位 : μT。 |


## PedometerResponse

计步传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称  | 类型   | 只读 | 可选 | 说明             |
| ----- | ------ | ---- | ---- | ---------------- |
| steps | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 用户的行走步数。 |


## HumidityResponse

湿度传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称     | 类型   | 只读 | 可选 | 说明                                                      |
| -------- | ------ | ---- | ---- | --------------------------------------------------------- |
| humidity | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 湿度值。测量环境的相对湿度，以百分比&nbsp;(%)&nbsp;表示。 |


## PedometerDetectionResponse

计步检测传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称   | 类型   | 只读 | 可选 | 说明                                                         |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| scalar | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 计步器检测。检测用户的计步动作，如果取值为1则代表用户产生了计步行走的动作，取值为0则代表用户没有发生运动。 |


## AmbientTemperatureResponse

温度传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称        | 类型   | 只读 | 可选 | 说明                       |
| ----------- | ------ | ---- | ---- | -------------------------- |
| temperature | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 环境温度（单位：摄氏度）。 |


## BarometerResponse

气压计传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称     | 类型   | 只读 | 可选 | 说明                   |
| -------- | ------ | ---- | ---- | ---------------------- |
| pressure | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 压力值（单位：百帕）。 |


## HeartRateResponse

心率传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称      | 类型   | 只读 | 可选 | 说明                                    |
| --------- | ------ | ---- | ---- | --------------------------------------- |
| heartRate | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 心率值。测量用户的心率数值，单位：bpm。 |


## WearDetectionResponse

佩戴检测传感器数据，继承于[Response](#response)。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23


| 名称  | 类型   | 只读 | 可选 | 说明                                             |
| ----- | ------ | ---- | ---- | ------------------------------------------------ |
| value | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 表示设备是否被穿戴（1表示已穿戴，0表示未穿戴）。 |


## Options

设置传感器上报频率。

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

| 名称     | 类型                                                        | 只读 | 可选 | 说明                                                                                         |
| -------- | ----------------------------------------------------------- | ---- | ---- |--------------------------------------------------------------------------------------------|
| interval | ArkTS-Dyn: number\|[SensorFrequency](#sensorfrequency11)<sup>11+</sup> <br> ArkTS-Sta: long\|[SensorFrequency](#sensorfrequency11)<sup>11+</sup> | 是   | 是   | 表示传感器的上报频率，默认值为200000000ns。该属性有最小值和最大值的限制，由硬件支持的上报频率决定，当设置频率大于最大值时以最大值上报数据，小于最小值时以最小值上报数据。 |
| sensorInfoParam<sup>19+</sup> | [SensorInfoParam](#sensorinfoparam19) | 是 | 是 | 传感器传入设置参数，可指定deviceId、sensorIndex。<br/>**原子化服务API**：从API Version 19开始，该接口支持在原子化服务中使用。                                                         |

## SensorFrequency<sup>11+</sup>

type SensorFrequency = 'game' | 'ui' | 'normal'

传感器上报频率模式。

**原子化服务API**：从API Version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Sensors.Sensor

| 类型     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| 'game'   | 用于指定传感器上报频率，频率值为20000000ns，该频率被设置在硬件支持的频率范围内时会生效，值固定为'game'字符串。 |
| 'ui'     | 用于指定传感器上报频率，频率值为60000000ns，该频率被设置在硬件支持的频率范围内时会生效，值固定为'ui'字符串。 |
| 'normal' | 用于指定传感器上报频率，频率值为200000000ns，该频率被设置在硬件支持的频率范围内时会生效，值固定为'normal'字符串。 |

## RotationMatrixResponse

设置旋转矩阵响应对象。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称        | 类型                | 只读 | 可选 | 说明       |
| ----------- | ------------------- | ---- | ---- | ---------- |
| rotation    | ArkTS-Dyn: Array&lt;number&gt; <br> ArkTS-Sta: Array&lt;double&gt; | 是   | 是   | 旋转矩阵。 |
| inclination | ArkTS-Dyn: Array&lt;number&gt; <br> ArkTS-Sta: Array&lt;double&gt; | 是   | 是   | 倾斜矩阵。 |


## CoordinatesOptions

设置坐标选项对象。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称 | 类型   | 只读 | 可选 | 说明        |
| ---- | ------ | ---- | ---- | ----------- |
| x    | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是   | 是   | x坐标方向。 |
| y    | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是   | 是   | y坐标方向。 |


## GeomagneticResponse

设置地磁响应对象。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称            | 类型   | 只读 | 可选 | 说明                                               |
| --------------- | ------ | ---- | ---- | -------------------------------------------------- |
| x               | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 地磁场的北分量。                                   |
| y               | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 地磁场的东分量。                                   |
| z               | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 地磁场的垂直分量。                                 |
| geomagneticDip  | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 地磁倾角，即地球磁场线与水平面的夹角。             |
| deflectionAngle | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 地磁偏角，即地磁北方向与正北方向在水平面上的角度。 |
| levelIntensity  | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 地磁场的水平强度。                                 |
| totalIntensity  | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 地磁场的总强度。                                   |

## LocationOptions

指示地理位置。

**系统能力**：SystemCapability.Sensors.Sensor

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称      | 类型   | 只读 | 可选 | 说明       |
| --------- | ------ | ---- | ---- | ---------- |
| latitude  | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 纬度。     |
| longitude | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 经度。     |
| altitude  | ArkTS-Dyn: number <br> ArkTS-Sta: double | 是   | 是   | 海拔高度。 |

## sensor.on<sup>(deprecated)</sup>

### ACCELEROMETER<sup>(deprecated)</sup>

on(type:  SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;,options?: Options): void

监听加速度传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.ACCELEROMETER](#accelerometer9)<sup>9+</sup>代替。

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER | 是   | 要订阅的加速度传感器类型为SENSOR_TYPE_ID_ACCELEROMETER。     |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | 是   | 注册加速度传感器的回调函数，上报的数据类型为AccelerometerResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER, (data: sensor.AccelerometerResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
},
  { interval: 100000000 }
);
```

### LINEAR_ACCELERATION<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION,callback:Callback&lt;LinearAccelerometerResponse&gt;, options?: Options): void

监听线性加速度传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.LINEAR_ACCELEROMETER](#linear_accelerometer9)<sup>9+</sup>代替。 

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_LINEAR_ACCELERATION | 是   | 要订阅的线性加速度传感器类型为SENSOR_TYPE_ID_LINEAR_ACCELERATION。 |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | 是   | 注册线性加速度传感器的回调函数，上报的数据类型为LinearAccelerometerResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

### ACCELEROMETER_UNCALIBRATED<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED,callback: Callback&lt;AccelerometerUncalibratedResponse&gt;, options?: Options): void

监听未校准加速度计传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.ACCELEROMETER_UNCALIBRATED](#accelerometer_uncalibrated9)<sup>9+</sup>代替。

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED | 是   | 要订阅的未校准加速度计传感器类型为SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED。 |
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | 是   | 注册未校准加速度计传感器的回调函数，上报的数据类型为AccelerometerUncalibratedResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
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

### GRAVITY<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback&lt;GravityResponse&gt;,options?: Options): void

监听重力传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.GRAVITY](#gravity9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                       | 必填 | 说明                                                        |
| -------- | ---------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GRAVITY | 是   | 要订阅的重力传感器类型为SENSOR_TYPE_ID_GRAVITY。            |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt;        | 是   | 注册重力传感器的回调函数，上报的数据类型为GravityResponse。 |
| options  | [Options](#options)                                        | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_GRAVITY, (data: sensor.GravityResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
},
  { interval: 100000000 }
);
```

### GYROSCOPE<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;, options?: Options): void

监听陀螺仪传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.GYROSCOPE](#gyroscope9)<sup>9+</sup>代替。

**需要权限**：ohos.permission.GYROSCOPE

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE | 是   | 要订阅的陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE。         |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt;      | 是   | 注册陀螺仪传感器的回调函数，上报的数据类型为GyroscopeResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE, (data: sensor.GyroscopeResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
},
  { interval: 100000000 }
);
```

### GYROSCOPE_UNCALIBRATED<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED,callback:Callback&lt;GyroscopeUncalibratedResponse&gt;, options?: Options): void

监听未校准陀螺仪传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.GYROSCOPE_UNCALIBRATED](#gyroscope_uncalibrated9)<sup>9+</sup>代替。

**需要权限**：ohos.permission.GYROSCOPE

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED | 是   | 要订阅的未校准陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED。 |
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | 是   | 注册未校准陀螺仪传感器的回调函数，上报的数据类型为GyroscopeUncalibratedResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
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

### SIGNIFICANT_MOTION<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;, options?: Options): void

监听有效运动传感器数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.SIGNIFICANT_MOTION](#significant_motion9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_SIGNIFICANT_MOTION | 是   | 要订阅的有效运动传感器类型为SENSOR_TYPE_ID_SIGNIFICANT_MOTION。 |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | 是   | 注册有效运动传感器的回调函数，上报的数据类型为SignificantMotionResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, (data: sensor.SignificantMotionResponse) => {
  console.info('Succeeded in invoking on. Scalar data: ' + data.scalar);
},
  { interval: 100000000 }
);
```

### PEDOMETER_DETECTION<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback: Callback&lt;PedometerDetectionResponse&gt;, options?: Options): void

监听计步检测传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.PEDOMETER_DETECTION](#pedometer_detection9)<sup>9+</sup>代替。 

**需要权限**：ohos.permission.ACTIVITY_MOTION

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER_DETECTION | 是   | 要订阅的计步检测传感器类型为SENSOR_TYPE_ID_PEDOMETER_DETECTION。 |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | 是   | 注册计步检测传感器的回调函数，上报的数据类型为PedometerDetectionResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
  console.info('Succeeded in invoking on. Scalar data: ' + data.scalar);
},
  { interval: 100000000 }
);
```

### PEDOMETER<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback&lt;PedometerResponse&gt;, options?: Options): void

监听计步传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.PEDOMETER](#pedometer9)<sup>9+</sup>代替。

**需要权限**：ohos.permission.ACTIVITY_MOTION 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER | 是   | 要订阅的计步传感器类型为SENSOR_TYPE_ID_PEDOMETER。           |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt;      | 是   | 注册计步传感器的回调函数，上报的数据类型为PedometerResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER, (data: sensor.PedometerResponse) => {
  console.info('Succeeded in invoking on. Steps: ' + data.steps);
},
  { interval: 100000000 }
);
```

### AMBIENT_TEMPERATURE<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE,callback:Callback&lt;AmbientTemperatureResponse&gt;,  options?: Options): void

监听环境温度传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.AMBIENT_TEMPERATURE](#ambient_temperature9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_TEMPERATURE | 是   | 要订阅的环境温度传感器类型为SENSOR_TYPE_ID_AMBIENT_TEMPERATURE。 |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | 是   | 注册环境温度传感器的回调函数，上报的数据类型为AmbientTemperatureResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
  console.info('Succeeded in invoking on. Temperature: ' + data.temperature);
},
  { interval: 100000000 }
);
```

### MAGNETIC_FIELD<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;,options?: Options): void

监听磁场传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.MAGNETIC_FIELD](#magnetic_field9)<sup>9+</sup>代替。  

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD | 是   | 要订阅的磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD。      |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | 是   | 注册磁场传感器的回调函数，上报的数据类型为MagneticFieldResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, (data: sensor.MagneticFieldResponse) => {
  console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
},
  { interval: 100000000 }
);
```

### MAGNETIC_FIELD_UNCALIBRATED<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED,callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;, options?: Options): void

监听未校准磁场传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.MAGNETIC_FIELD_UNCALIBRATED](#magnetic_field_uncalibrated9)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | 是   | 要订阅的未校准磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | 是   | 注册未校准磁场传感器的回调函数，上报的数据类型为MagneticFieldUncalibratedResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
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

### PROXIMITY<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback&lt;ProximityResponse&gt;,options?: Options): void

监听接近光传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.PROXIMITY](#proximity9)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PROXIMITY | 是   | 要订阅的接近光传感器类型为SENSOR_TYPE_ID_PROXIMITY。         |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt;      | 是   | 注册接近光传感器的回调函数，上报的数据类型为ProximityResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，默认值为200000000ns。当接近光事件被触发的很频繁时，该参数用于限定事件上报的频率。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PROXIMITY, (data: sensor.ProximityResponse) => {
  console.info('Succeeded in invoking on. Distance: ' + data.distance);
},
  { interval: 100000000 }
);
```

### HUMIDITY<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback&lt;HumidityResponse&gt;,options?: Options): void

监听湿度传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.HUMIDITY](#humidity9)<sup>9+</sup>代替。  

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HUMIDITY | 是   | 要订阅的湿度传感器类型为SENSOR_TYPE_ID_HUMIDITY。            |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt;       | 是   | 注册湿度传感器的回调函数，上报的数据类型为HumidityResponse。 |
| options  | [Options](#options)                                         | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_HUMIDITY, (data: sensor.HumidityResponse) => {
  console.info('Succeeded in invoking on. Humidity: ' + data.humidity);
},
  { interval: 100000000 }
);
```

### BAROMETER<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback&lt;BarometerResponse&gt;,options?: Options): void

监听气压计传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.BAROMETER](#barometer9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_BAROMETER | 是   | 要订阅的气压计传感器类型为SENSOR_TYPE_ID_BAROMETER。         |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt;      | 是   | 注册气压计传感器的回调函数，上报的数据类型为BarometerResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_BAROMETER, (data: sensor.BarometerResponse) => {
  console.info('Succeeded in invoking on. Atmospheric pressure: ' + data.pressure);
},
  { interval: 100000000 }
);
```

### HALL<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback&lt;HallResponse&gt;, options?: Options): void

监听霍尔传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.HALL](#hall9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HALL | 是   | 要订阅的霍尔传感器类型为SENSOR_TYPE_ID_HALL。                |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt;           | 是   | 注册霍尔传感器的回调函数，上报的数据类型为&nbsp;HallResponse。 |
| options  | [Options](#options)                                     | 否   | 可选参数列表，默认值为200000000ns。当霍尔事件被触发的很频繁时，该参数用于限定事件上报的频率。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_HALL, (data: sensor.HallResponse) => {
  console.info('Succeeded in invoking on. Status: ' + data.status);
},
  { interval: 100000000 }
);
```

### AMBIENT_LIGHT<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;, options?: Options): void

监听环境光传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.AMBIENT_LIGHT](#ambient_light9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                        |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_LIGHT | 是   | 要订阅的环境光传感器类型为SENSOR_TYPE_ID_AMBIENT_LIGHT。    |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt;              | 是   | 注册环境光传感器的回调函数，上报的数据类型为LightResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, (data: sensor.LightResponse) => {
  console.info('Succeeded in invoking on. Illumination: ' + data.intensity);
},
  { interval: 100000000 }
);
```

### ORIENTATION<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback&lt;OrientationResponse&gt;, options?: Options): void

监听方向传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.ORIENTATION](#orientation9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ORIENTATION | 是   | 要订阅的方向传感器类型为SENSOR_TYPE_ID_ORIENTATION。         |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt;  | 是   | 注册方向传感器的回调函数，上报的数据类型为OrientationResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_ORIENTATION, (data: sensor.OrientationResponse) => {
  console.info('Succeeded in the device rotating at an angle around the X axis: ' + data.beta);
  console.info('Succeeded in the device rotating at an angle around the Y axis: ' + data.gamma);
  console.info('Succeeded in the device rotating at an angle around the Z axis: ' + data.alpha);
},
  { interval: 100000000 }
);
```

### HEART_RATE<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;, options?: Options): void

监听心率传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.HEART_RATE](#heart_rate9)<sup>9+</sup>代替。

**需要权限**：ohos.permission.HEALTH_DATA 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HEART_RATE | 是   | 要订阅的心率传感器类型为SENSOR_TYPE_ID_HEART_RATE。          |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt;      | 是   | 注册心率传感器的回调函数，上报的数据类型为HeartRateResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

### ROTATION_VECTOR<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR,callback: Callback&lt;RotationVectorResponse&gt;,options?: Options): void

监听旋转矢量传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.ROTATION_VECTOR](#rotation_vector9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ROTATION_VECTOR | 是   | 要订阅的旋转矢量传感器类型为SENSOR_TYPE_ID_ROTATION_VECTOR。 |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | 是   | 注册旋转矢量传感器的回调函数，上报的数据类型为RotationVectorResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
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

### WEAR_DETECTION<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;,options?: Options): void

监听所佩戴的检测传感器的数据变化。如果多次调用该接口，仅最后一次调用生效。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.on.WEAR_DETECTION](#wear_detection9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_WEAR_DETECTION | 是   | 要订阅的佩戴检测传感器类型为SENSOR_TYPE_ID_WEAR_DETECTION。  |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | 是   | 注册佩戴检测传感器的回调函数，上报的数据类型为WearDetectionResponse。 |
| options  | [Options](#options)                                          | 否   | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns。  |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, (data: sensor.WearDetectionResponse) => {
  console.info('Succeeded in invoking on. Wear status: ' + data.value);
},
  { interval: 100000000 }
);
```

## sensor.once<sup>(deprecated)</sup>

### ACCELEROMETER<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;): void

监听加速度传感器的数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.ACCELEROMETER](#accelerometer9-1)<sup>9+</sup>代替。

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER | 是   | 加速度传感器类型为SENSOR_TYPE_ID_ACCELEROMETER。             |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | 是   | 注册一次加速度传感器的回调函数，上报的数据类型为AccelerometerResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER, (data: sensor.AccelerometerResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
});
```

### LINEAR_ACCELERATION<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION,callback:Callback&lt;LinearAccelerometerResponse&gt;): void

监听线性加速度传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.LINEAR_ACCELEROMETER](#linear_accelerometer9-1)<sup>9+</sup>代替。

**需要权限**：ohos.permission.ACCELERATION

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_LINEAR_ACCELERATION | 是   | 线性加速度传感器类型为SENSOR_TYPE_ID_LINEAR_ACCELERATION。   |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | 是   | 注册一次线性加速度传感器的回调函数，上报的数据类型为LinearAccelerometerResponse。 |

### ACCELEROMETER_UNCALIBRATED<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED,callback: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

监听未校准加速度传感器的数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.ACCELEROMETER_UNCALIBRATED](#accelerometer_uncalibrated9-1)<sup>9+</sup>代替。

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED | 是   | 未校准加速度传感器类型为SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED。 |
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | 是   | 注册一次未校准加速度传感器的回调函数，上报的数据类型为AccelerometerUncalibratedResponse。 |

**示例**：

```ts
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

### GRAVITY<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback&lt;GravityResponse&gt;): void

监听重力传感器的数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.GRAVITY](#gravity9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                       | 必填 | 说明                                                         |
| -------- | ---------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GRAVITY | 是   | 重力传感器类型为SENSOR_TYPE_ID_GRAVITY。                     |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt;        | 是   | 注册一次重力传感器的回调函数，上报的数据类型为GravityResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_GRAVITY, (data: sensor.GravityResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  });
```

### GYROSCOPE<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;): void

监听陀螺仪传感器的数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.GYROSCOPE](#gyroscope9-1)<sup>9+</sup>代替。

**需要权限**：ohos.permission.GYROSCOPE

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE | 是   | 陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE。                 |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt;      | 是   | 注册一次陀螺仪传感器的回调函数，上报的数据类型为GyroscopeResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE, (data: sensor.GyroscopeResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
});
```

### GYROSCOPE_UNCALIBRATED<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED,callback: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

监听未校准陀螺仪传感器的数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.GYROSCOPE_UNCALIBRATED](#gyroscope_uncalibrated9-1)<sup>9+</sup>代替。

**需要权限**：ohos.permission.GYROSCOPE

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED | 是   | 未校准陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED。 |
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | 是   | 注册一次未校准陀螺仪传感器的回调函数，上报的数据类型为GyroscopeUncalibratedResponse。 |

**示例**：


```ts
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

### SIGNIFICANT_MOTION<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION,callback: Callback&lt;SignificantMotionResponse&gt;): void

监听有效运动传感器的数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.SIGNIFICANT_MOTION](#significant_motion9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_SIGNIFICANT_MOTION | 是   | 有效运动传感器类型为SENSOR_TYPE_ID_SIGNIFICANT_MOTION。      |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | 是   | 注册一次有效运动传感器的回调函数，上报的数据类型为SignificantMotionResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, (data: sensor.SignificantMotionResponse) => {
  console.info('Succeeded in invoking once. Scalar data: ' + data.scalar);
});
```

### PEDOMETER_DETECTION<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION,callback: Callback&lt;PedometerDetectionResponse&gt;): void

监听计步检测传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.PEDOMETER_DETECTION](#pedometer_detection9-1)<sup>9+</sup>代替。

**需要权限**：ohos.permission.ACTIVITY_MOTION

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER_DETECTION | 是   | 计步检测传感器类型为SENSOR_TYPE_ID_PEDOMETER_DETECTION。     |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | 是   | 注册一次计步检测传感器的回调函数，上报的数据类型为PedometerDetectionResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
  console.info('Succeeded in invoking once. Scalar data: ' + data.scalar);
});
```

### PEDOMETER<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback&lt;PedometerResponse&gt;): void

监听计步器传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.PEDOMETER](#pedometer9-1)<sup>9+</sup>代替。

**需要权限**：ohos.permission.ACTIVITY_MOTION

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER | 是   | 计步传感器类型为SENSOR_TYPE_ID_PEDOMETER。                   |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt;      | 是   | 注册一次计步传感器的回调函数，上报的数据类型为PedometerResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER, (data: sensor.PedometerResponse) => {
  console.info('Succeeded in invoking once. Steps: ' + data.steps);
});
```

### AMBIENT_TEMPERATURE<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE,callback: Callback&lt;AmbientTemperatureResponse&gt;): void

监听环境温度传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.AMBIENT_TEMPERATURE](#ambient_temperature9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_TEMPERATURE | 是   | 环境温度传感器类型为SENSOR_TYPE_ID_AMBIENT_TEMPERATURE。     |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | 是   | 注册一次环境温度传感器的回调函数，上报的数据类型为AmbientTemperatureResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
  console.info('Succeeded in invoking once. Temperature: ' + data.temperature);
});
```

### MAGNETIC_FIELD<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;): void

监听磁场传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.MAGNETIC_FIELD](#magnetic_field9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD | 是   | 磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD。              |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | 是   | 注册一次磁场传感器的回调函数，上报的数据类型为MagneticFieldResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, (data: sensor.MagneticFieldResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
});
```

### MAGNETIC_FIELD_UNCALIBRATED<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED,callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

监听未校准磁场传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.MAGNETIC_FIELD_UNCALIBRATED](#magnetic_field_uncalibrated9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | 是   | 未校准磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | 是   | 注册一次未校准磁场传感器的回调函数，上报的数据类型为MagneticFieldUncalibratedResponse。 |

**示例**：

```ts
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

### PROXIMITY<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback&lt;ProximityResponse&gt;): void

监听接近光传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.PROXIMITY](#proximity9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PROXIMITY | 是   | 接近光传感器类型为SENSOR_TYPE_ID_PROXIMITY。                 |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt;      | 是   | 注册一次接近光传感器的回调函数，上报的数据类型为ProximityResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_PROXIMITY, (data: sensor.ProximityResponse) => {
  console.info('Succeeded in invoking once. Distance: ' + data.distance);
}
);
```

### HUMIDITY<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback&lt;HumidityResponse&gt;): void

监听湿度传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.HUMIDITY](#humidity9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HUMIDITY | 是   | 湿度传感器类型为SENSOR_TYPE_ID_HUMIDITY。                    |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt;       | 是   | 注册一次湿度传感器的回调函数，上报的数据类型为HumidityResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_HUMIDITY, (data: sensor.HumidityResponse) => {
  console.info('Succeeded in invoking once. Humidity: ' + data.humidity);
});
```

### BAROMETER<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback&lt;BarometerResponse&gt;): void

监听气压计传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.BAROMETER](#barometer9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_BAROMETER | 是   | 气压计传感器类型为SENSOR_TYPE_ID_BAROMETER。                 |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt;      | 是   | 注册一次气压计传感器的回调函数，上报的数据类型为BarometerResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_BAROMETER, (data: sensor.BarometerResponse) => {
  console.info('Succeeded in invoking once. Atmospheric pressure: ' + data.pressure);
});
```

### HALL<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback&lt;HallResponse&gt;): void

监听霍尔传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.HALL](#hall9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HALL | 是   | 霍尔传感器类型为SENSOR_TYPE_ID_HALL。                        |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt;           | 是   | 注册一次霍尔传感器的回调函数，上报的数据类型为HallResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_HALL, (data: sensor.HallResponse) => {
  console.info('Succeeded in invoking once. Status: ' + data.status);
});
```

### AMBIENT_LIGHT<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;): void

监听环境光传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.AMBIENT_LIGHT](#ambient_light9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_LIGHT | 是   | 环境光传感器类型为SENSOR_TYPE_ID_AMBIENT_LIGHT。             |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt;              | 是   | 注册一次环境光传感器的回调函数，上报的数据类型为LightResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, (data: sensor.LightResponse) => {
  console.info('Succeeded in invoking once. invoking once. Illumination: ' + data.intensity);
});
```

### ORIENTATION<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback&lt;OrientationResponse&gt;): void

监听方向传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.ORIENTATION](#orientation9-1)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ORIENTATION | 是   | 方向传感器类型为SENSOR_TYPE_ID_ORIENTATION。                 |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt;  | 是   | 注册一次方向传感器的回调函数，上报的数据类型为OrientationResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_ORIENTATION, (data: sensor.OrientationResponse) => {
  console.info('Succeeded in invoking the device rotateing at an angle around the X axis: ' + data.beta);
  console.info('Succeeded in invoking the device rotateing at an angle around the Y axis: ' + data.gamma);
  console.info('Succeeded in invoking the device rotateing at an angle around the Z axis: ' + data.alpha);
});
```

### ROTATION_VECTOR<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;): void

监听旋转矢量传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.ROTATION_VECTOR](#rotation_vector9-1)<sup>9+</sup>代替。  

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ROTATION_VECTOR | 是   | 旋转矢量传感器类型为SENSOR_TYPE_ID_ROTATION_VECTOR。         |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | 是   | 注册一次旋转矢量传感器的回调函数，上报的数据类型为RotationVectorResponse。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, (data: sensor.RotationVectorResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking once. Scalar quantity: ' + data.w);
});
```

### HEART_RATE<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;): void

监听心率传感器数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.HEART_RATE](#heart_rate9-1)<sup>9+</sup>代替。

**需要权限**：ohos.permission.HEART_RATE  

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HEART_RATE | 是   | 心率传感器类型为SENSOR_TYPE_ID_HEART_RATE。                  |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt;      | 是   | 注册一次心率传感器的回调函数，上报的数据类型为HeartRateResponse。 |

**示例**：


```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_HEART_RATE, (data: sensor.HeartRateResponse) => {
  console.info("Succeeded in invoking once. Heart rate: " + data.heartRate);
});
```

### WEAR_DETECTION<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;): void

监听所佩戴的检测传感器的数据变化一次。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.once.WEAR_DETECTION](#wear_detection9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_WEAR_DETECTION | 是   | 佩戴检测传感器类型为SENSOR_TYPE_ID_WEAR_DETECTION。          |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | 是   | 注册一次穿戴检测传感器的回调函数，上报的数据类型为WearDetectionResponse。 |

**示例**：


```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, (data: sensor.WearDetectionResponse) => {
  console.info("Succeeded in invoking once. Wear status: " + data.value);
});
```

## sensor.off<sup>(deprecated)</sup>

### ACCELEROMETER<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback?: Callback&lt;AccelerometerResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.ACCELEROMETER<sup>9+</sup>](#accelerometer9-2)代替。

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER | 是   | 要取消订阅的加速度传感器类型为SENSOR_TYPE_ID_ACCELEROMETER。 |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.AccelerometerResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback);
```

### ACCELEROMETER_UNCALIBRATED<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback?: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.ACCELEROMETER_UNCALIBRATED](#accelerometer_uncalibrated9-2)<sup>9+</sup>代替。 

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED | 是   | 要取消订阅的未校准加速度计传感器类型为SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED。 |
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.AccelerometerUncalibratedResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking off. X-coordinate bias: ' + data.biasX);
  console.info('Succeeded in invoking off. Y-coordinate bias: ' + data.biasY);
  console.info('Succeeded in invoking off. Z-coordinate bias: ' + data.biasZ);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback);
```

### AMBIENT_LIGHT<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback?: Callback&lt;LightResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.AMBIENT_LIGHT](#ambient_light9-2)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_LIGHT | 是   | 要取消订阅的环境光传感器类型为SENSOR_TYPE_ID_AMBIENT_LIGHT。 |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt;              | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.LightResponse) {
  console.info('Succeeded in invoking off. Illumination: ' + data.intensity);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback);
```

### AMBIENT_TEMPERATURE<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback?: Callback&lt;AmbientTemperatureResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.AMBIENT_TEMPERATURE](#ambient_temperature9-2)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_TEMPERATURE | 是   | 要取消订阅的环境温度传感器类型为SENSOR_TYPE_ID_AMBIENT_TEMPERATURE。 |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.AmbientTemperatureResponse) {
  console.info('Succeeded in invoking off. Temperature: ' + data.temperature);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback);
```

### BAROMETER<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback?: Callback&lt;BarometerResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.BAROMETER](#barometer9-2)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_BAROMETER | 是   | 要取消订阅的气压计传感器类型为SENSOR_TYPE_ID_BAROMETER。     |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt;      | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.BarometerResponse) {
  console.info('Succeeded in invoking off. Atmospheric pressure: ' + data.pressure);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_BAROMETER, callback);
```

### GRAVITY<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback?: Callback&lt;GravityResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.GRAVITY](#gravity9-2)<sup>9+</sup>代替。  

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                       | 必填 | 说明                                                         |
| -------- | ---------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GRAVITY | 是   | 要取消订阅的重力传感器类型为SENSOR_TYPE_ID_GRAVITY。         |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt;        | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.GravityResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_GRAVITY, callback);
```

### GYROSCOPE<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback?: Callback&lt;GyroscopeResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.GYROSCOPE](#gyroscope9-2)<sup>9+</sup>代替。 

**需要权限**：ohos.permission.GYROSCOPE

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE | 是   | 要取消订阅的陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE。     |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt;      | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.GyroscopeResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback);
```

### GYROSCOPE_UNCALIBRATED<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback?: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.GYROSCOPE_UNCALIBRATED](#gyroscope_uncalibrated9-2)<sup>9+</sup>代替。

**需要权限**：ohos.permission.GYROSCOPE

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED | 是   | 要取消订阅的未校准陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED。 |
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.GyroscopeUncalibratedResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback);
```

### HALL<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_HALL, callback?: Callback&lt;HallResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.HALL](#hall9-2)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HALL | 是   | 要取消订阅的霍尔传感器类型为SENSOR_TYPE_ID_HALL。            |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt;           | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.HallResponse) {
  console.info('Succeeded in invoking off. Status: ' + data.status);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_HALL, callback);
```

### HEART_RATE<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback?: Callback&lt;HeartRateResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.HEART_RATE](#heart_rate9-2)<sup>9+</sup>代替。

**需要权限**：ohos.permission.HEALTH_DATA 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HEART_RATE | 是   | 要取消订阅的心率传感器类型为SENSOR_TYPE_ID_HEART_RATE。      |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt;      | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.HeartRateResponse) {
  console.info('Succeeded in invoking off. Humidity: ' + data.heartRate);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_HEART_RATE, callback);
```

### HUMIDITY<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback?: Callback&lt;HumidityResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.HUMIDITY](#humidity9-2)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HUMIDITY | 是   | 要取消订阅的湿度传感器类型为SENSOR_TYPE_ID_HUMIDITY。        |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt;       | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.HumidityResponse) {
  console.info('Succeeded in invoking off. Humidity: ' + data.humidity);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_HUMIDITY, callback);
```

### LINEAR_ACCELERATION<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback?: Callback&lt;LinearAccelerometerResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.LINEAR_ACCELEROMETER](#linear_accelerometer9-2)<sup>9+</sup>代替。

**需要权限**：ohos.permission.ACCELEROMETER

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_LINEAR_ACCELERATION | 是   | 要取消订阅的线性加速度传感器类型为SENSOR_TYPE_ID_LINEAR_ACCELERATION。 |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.LinearAccelerometerResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback);
```

### MAGNETIC_FIELD<sup>(deprecated)</sup>

 off(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback?: Callback&lt;MagneticFieldResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.MAGNETIC_FIELD](#magnetic_field9-2)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD | 是   | 要取消订阅的磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD。  |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.MagneticFieldResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback);
```

### MAGNETIC_FIELD_UNCALIBRATED<sup>(deprecated)</sup>

 off(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback?: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.MAGNETIC_FIELD_UNCALIBRATED](#magnetic_field_uncalibrated9-2)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | 是   | 要取消订阅的未校准磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.MagneticFieldUncalibratedResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking off. X-coordinate bias: ' + data.biasX);
  console.info('Succeeded in invoking off. Y-coordinate bias: ' + data.biasY);
  console.info('Succeeded in invoking off. Z-coordinate bias: ' + data.biasZ);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback);
```

### ORIENTATION<sup>(deprecated)</sup>

 off(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback?: Callback&lt;OrientationResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.ORIENTATION](#orientation9-2)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ORIENTATION | 是   | 要取消订阅的方向传感器类型为SENSOR_TYPE_ID_ORIENTATION。     |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt;  | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.OrientationResponse) {
  console.info('Succeeded in invoking off. The device rotates at an angle around the X axis: ' + data.beta);
  console.info('Succeeded in invoking off. The device rotates at an angle around the Y axis: ' + data.gamma);
  console.info('Succeeded in invoking off. The device rotates at an angle around the Z axis: ' + data.alpha);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_ORIENTATION, callback);
```

### PEDOMETER<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback?: Callback&lt;PedometerResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.PEDOMETER](#pedometer9-2)<sup>9+</sup>代替。 

**需要权限**：ohos.permission.ACTIVITY_MOTION

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER | 是   | 要取消订阅的计步传感器类型为SENSOR_TYPE_ID_PEDOMETER。       |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt;      | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.PedometerResponse) {
  console.info('Succeeded in invoking off. Steps: ' + data.steps);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER, callback);
```

### PEDOMETER_DETECTION<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback?: Callback&lt;PedometerDetectionResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.PEDOMETER_DETECTION](#pedometer_detection9-2)<sup>9+</sup>代替。 

**需要权限**：ohos.permission.ACTIVITY_MOTION

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER_DETECTION | 是   | 要取消订阅的计步检测传感器类型为SENSOR_TYPE_ID_PEDOMETER_DETECTION。 |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.PedometerDetectionResponse) {
  console.info('Succeeded in invoking off. Scalar data: ' + data.scalar);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback);
```

### PROXIMITY<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback?: Callback&lt;ProximityResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.PROXIMITY](#proximity9-2)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PROXIMITY | 是   | 要取消订阅的接近光传感器类型为SENSOR_TYPE_ID_PROXIMITY。     |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt;      | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.ProximityResponse) {
  console.info('Succeeded in invoking off. Distance: ' + data.distance);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_PROXIMITY, callback);
```

### ROTATION_VECTOR<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback?: Callback&lt;RotationVectorResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.ROTATION_VECTOR](#rotation_vector9-2)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ROTATION_VECTOR | 是   | 要取消订阅的旋转矢量传感器类型为SENSOR_TYPE_ID_ROTATION_VECTOR。 |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.RotationVectorResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking off. Scalar quantity: ' + data.w);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback);
```

### SIGNIFICANT_MOTION<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback?: Callback&lt;SignificantMotionResponse&gt;): void

取消订阅有效运动传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.SIGNIFICANT_MOTION](#significant_motion9-2)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_SIGNIFICANT_MOTION | 是   | 要取消订阅的有效运动传感器类型为SENSOR_TYPE_ID_SIGNIFICANT_MOTION。 |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.SignificantMotionResponse) {
  console.info('Succeeded in invoking off. Scalar data: ' + data.scalar);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback);
```

### WEAR_DETECTION<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback?: Callback&lt;WearDetectionResponse&gt;): void

取消订阅传感器数据。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.off.WEAR_DETECTION](#wear_detection9-2)<sup>9+</sup>代替。 

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_WEAR_DETECTION | 是   | 要取消订阅的佩戴检测传感器类型为SENSOR_TYPE_ID_WEAR_DETECTION。 |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | 否   | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';

function accCallback(data: sensor.WearDetectionResponse) {
  console.info('Succeeded in invoking off. Wear status: ' + data.value);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, accCallback);
```

## sensor.transformCoordinateSystem<sup>(deprecated)</sup>

transformCoordinateSystem(inRotationVector: Array&lt;number&gt;, coordinates: CoordinatesOptions, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

旋转提供的旋转矩阵，使其可以以不同的方式表示坐标系，使用Callback异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.transformRotationMatrix](#sensortransformrotationmatrix9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名           | 类型                                      | 必填 | 说明                       |
| ---------------- | ----------------------------------------- | ---- | -------------------------- |
| inRotationVector | Array&lt;number&gt;                       | 是   | 表示旋转矩阵。             |
| coordinates      | [CoordinatesOptions](#coordinatesoptions) | 是   | 表示坐标系方向。           |
| callback         | AsyncCallback&lt;Array&lt;number&gt;&gt;  | 是   | 异步返回转换后的旋转矩阵。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.transformCoordinateSystem([1, 0, 0, 0, 1, 0, 0, 0, 1], { x: 2, y: 3 }, 
                                 (err: BusinessError, data: Array<number>) => {
  if (err) {
    console.error(`Failed to operate. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info("Succeeded in starting Operation. Data obtained: " + data);
  for (let i = 0; i < data.length; i++) {
    console.info("Succeeded in getting transformCoordinateSystem data[ " + i + "] = " + data[i]);
  }
})
```
## sensor.transformCoordinateSystem<sup>(deprecated)</sup>

transformCoordinateSystem(inRotationVector: Array&lt;number&gt;, coordinates: CoordinatesOptions): Promise&lt;Array&lt;number&gt;&gt;

旋转提供的旋转矩阵，使其可以以不同的方式表示坐标系，使用Promise异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.transformRotationMatrix](#sensortransformrotationmatrix9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名              | 类型                                       | 必填   | 说明       |
| ---------------- | ---------------------------------------- | ---- | -------- |
| inRotationVector | Array&lt;number&gt;                      | 是    | 表示旋转矩阵。  |
| coordinates      | [CoordinatesOptions](#coordinatesoptions) | 是    | 表示坐标系方向。 |

**返回值**：

| 类型                               | 说明                               |
| ---------------------------------- | ---------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | 使用异步方式返回转换后的旋转矩阵。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.transformCoordinateSystem([1, 0, 0, 0, 1, 0, 0, 0, 1], { x: 2, y: 3 });
promise.then((data: Array<number>) => {
  console.info("Succeeded in starting Operation");
  for (let i = 0; i < data.length; i++) {
    console.info("Succeeded in getting transformCoordinateSystem data[ " + i + "] = " + data[i]);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to operate.`);
})
```

## sensor.getGeomagneticField<sup>(deprecated)</sup>

getGeomagneticField(locationOptions: LocationOptions, timeMillis: number, callback: AsyncCallback&lt;GeomagneticResponse&gt;): void

获取地球上特定位置的地磁场，使用callback异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getGeomagneticInfo](#sensorgetgeomagneticinfo9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名          | 类型                                                         | 必填 | 说明                               |
| --------------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| locationOptions | [LocationOptions](#locationoptions)                          | 是   | 地理位置。                         |
| timeMillis      | number                                                       | 是   | 表示获取磁偏角的时间，单位为毫秒。 |
| callback        | AsyncCallback&lt;[GeomagneticResponse](#geomagneticresponse)&gt; | 是   | 异步返回磁场信息。                 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.getGeomagneticField({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000, 
                           (err: BusinessError, data: sensor.GeomagneticResponse) => {
  if (err) {
    console.error(`Failed to operate. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting sensor_getGeomagneticField_callback x: ' + data.x + ',y: ' + data.y + ',z: ' +
  data.z + ',geomagneticDip: ' + data.geomagneticDip + ',deflectionAngle: ' + data.deflectionAngle +
  ',levelIntensity: ' + data.levelIntensity + ',totalIntensity: ' + data.totalIntensity);
});
```
## sensor.getGeomagneticField<sup>(deprecated)</sup>

getGeomagneticField(locationOptions: LocationOptions, timeMillis: number): Promise&lt;GeomagneticResponse&gt;

获取地球上特定位置的地磁场，使用Promise异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getGeomagneticInfo](#sensorgetgeomagneticinfo9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名             | 类型                                  | 必填   | 说明                |
| --------------- | ----------------------------------- | ---- | ----------------- |
| locationOptions | [LocationOptions](#locationoptions) | 是    | 地理位置。             |
| timeMillis      | number                              | 是    | 表示获取磁偏角的时间，单位为毫秒。 |

**返回值**：

| 类型                                                       | 说明                       |
| ---------------------------------------------------------- | -------------------------- |
| Promise&lt;[GeomagneticResponse](#geomagneticresponse)&gt; | 使用异步方式返回磁场信息。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getGeomagneticField({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000);
promise.then((data: sensor.GeomagneticResponse) => {
  console.info('Succeeded in getting sensor_getGeomagneticField_promise x: ' + data.x + ',y: ' + data.y + ',z: ' +
  data.z + ',geomagneticDip: ' + data.geomagneticDip + ',deflectionAngle: ' + data.deflectionAngle +
  ',levelIntensity: ' + data.levelIntensity + ',totalIntensity: ' + data.totalIntensity);
}).catch((reason: BusinessError) => {
  console.error(`Failed to operate.`);
})
```

## sensor.getAltitude<sup>(deprecated)</sup>

getAltitude(seaPressure: number, currentPressure: number, callback: AsyncCallback&lt;number&gt;): void

根据气压值获取设备所在的海拔高度，使用Callback异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getDeviceAltitude](#sensorgetdevicealtitude9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名          | 类型                        | 必填 | 说明                                   |
| --------------- | --------------------------- | ---- | -------------------------------------- |
| seaPressure     | number                      | 是   | 表示海平面气压值，单位为hPa。          |
| currentPressure | number                      | 是   | 表示设备所在高度的气压值，单位为hPa。  |
| callback        | AsyncCallback&lt;number&gt; | 是   | 异步返回设备所在的海拔高度，单位为米。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.getAltitude(0, 200, (err: BusinessError, data: number) => {
  if (err) {
    console.error(`Failed to operate. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info("Succeeded in getting getAltitude interface get data: " + data);
});
```

## sensor.getAltitude<sup>(deprecated)</sup>

getAltitude(seaPressure: number, currentPressure: number): Promise&lt;number&gt;

根据气压值获取设备所在的海拔高度，使用Promise异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getDeviceAltitude](#sensorgetdevicealtitude9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名             | 类型     | 必填   | 说明                   |
| --------------- | ------ | ---- | -------------------- |
| seaPressure     | number | 是    | 表示海平面气压值，单位为hPa。     |
| currentPressure | number | 是    | 表示设备所在高度的气压值，单位为hPa。 |

**返回值**：

| 类型                  | 说明                                             |
| --------------------- | ------------------------------------------------ |
| Promise&lt;number&gt; | 使用异步方式返回设备所在的海拔高度（单位：米）。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getAltitude(0, 200);
promise.then((data: number) => {
  console.info('Succeeded in getting sensor_getAltitude_Promise success', data);
}).catch((err: BusinessError) => {
  console.error(`Failed to operate.`);
})
```


## sensor.getGeomagneticDip<sup>(deprecated)</sup>

getGeomagneticDip(inclinationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;number&gt;): void

根据倾斜矩阵计算地磁倾斜角，使用Callback异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getInclination](#sensorgetinclination9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名            | 类型                        | 必填 | 说明                             |
| ----------------- | --------------------------- | ---- | -------------------------------- |
| inclinationMatrix | Array&lt;number&gt;         | 是   | 表示倾斜矩阵。                   |
| callback          | AsyncCallback&lt;number&gt; | 是   | 异步返回地磁倾斜角，单位为弧度。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.getGeomagneticDip([1, 0, 0, 0, 1, 0, 0, 0, 1], (err: BusinessError, data: number) => {
  if (err) {
    console.error(`Failed to register data. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info("Succeeded in getting getGeomagneticDip interface get data: " + data);
})
```

## sensor.getGeomagneticDip<sup>(deprecated)</sup>

getGeomagneticDip(inclinationMatrix: Array&lt;number&gt;): Promise&lt;number&gt;

根据倾斜矩阵计算地磁倾斜角，使用Promise异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getInclination](#sensorgetinclination9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名               | 类型                  | 必填   | 说明      |
| ----------------- | ------------------- | ---- | ------- |
| inclinationMatrix | Array&lt;number&gt; | 是    | 表示倾斜矩阵。 |

**返回值**：

| 类型                  | 说明                                     |
| --------------------- | ---------------------------------------- |
| Promise&lt;number&gt; | 使用异步方式返回地磁倾斜角，单位为弧度。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getGeomagneticDip([1, 0, 0, 0, 1, 0, 0, 0, 1]);
promise.then((data: number) => {
  console.info('Succeeded in get GeomagneticDip_promise', data);
}).catch((err: BusinessError) => {
  console.error(`Failed to operate.`);
})
```

## sensor. getAngleModify<sup>(deprecated)</sup>

getAngleModify(currentRotationMatrix: Array&lt;number&gt;, preRotationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

获取两个旋转矩阵之间的角度变化，使用Callback异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getAngleVariation](#sensorgetanglevariation9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名                | 类型                                     | 必填 | 说明                                  |
| --------------------- | ---------------------------------------- | ---- | ------------------------------------- |
| currentRotationMatrix | Array&lt;number&gt;                      | 是   | 表示当前旋转矩阵。                    |
| preRotationMatrix     | Array&lt;number&gt;                      | 是   | 表示旋转矩阵。                        |
| callback              | AsyncCallback&lt;Array&lt;number&gt;&gt; | 是   | 异步返回z、x、y轴方向的旋转角度变化。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.getAngleModify([1, 0, 0, 0, 1, 0, 0, 0, 1], [1, 0, 0, 0, 0.87, -0.50, 0, 0.50, 0.87],
                      (err: BusinessError, data: Array<number>) => {
  if (err) {
    console.error(`Failed to register data. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  for (let i = 0; i < data.length; i++) {
    console.info("data[" + i + "]: " + data[i]);
  }
})
```

## sensor. getAngleModify<sup>(deprecated)</sup>

getAngleModify(currentRotationMatrix: Array&lt;number&gt;, preRotationMatrix: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

获取两个旋转矩阵之间的角度变化，使用Promise异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getAngleVariation](#sensorgetanglevariation9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名                   | 类型                  | 必填   | 说明        |
| --------------------- | ------------------- | ---- | --------- |
| currentRotationMatrix | Array&lt;number&gt; | 是    | 表示当前旋转矩阵。 |
| preRotationMatrix     | Array&lt;number&gt; | 是    | 表示旋转矩阵。   |

**返回值**：

| 类型                               | 说明                                          |
| ---------------------------------- | --------------------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | 使用异步方式返回z、x、y轴方向的旋转角度变化。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getAngleModify([1, 0, 0, 0, 1, 0, 0, 0, 1], [1, 0, 0, 0, 0.87, -0.50, 0, 0.50, 0.87]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting AngleModify_promise.');
  for (let i = 0; i < data.length; i++) {
    console.info("Succeeded in getting data[" + i + "]: " + data[i]);
  }
}).catch((reason: BusinessError) => {
  let e: BusinessError = reason as BusinessError;
  console.info("Succeeded in getting promise::catch", e);
})
```

## sensor.createRotationMatrix<sup>(deprecated)</sup>

createRotationMatrix(rotationVector: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

将旋转矢量转换为旋转矩阵，使用Callback异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getRotationMatrix](#sensorgetrotationmatrix9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名         | 类型                                     | 必填 | 说明               |
| -------------- | ---------------------------------------- | ---- | ------------------ |
| rotationVector | Array&lt;number&gt;                      | 是   | 表示旋转矢量。     |
| callback       | AsyncCallback&lt;Array&lt;number&gt;&gt; | 是   | 异步返回旋转矩阵。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.createRotationMatrix([0.20046076, 0.21907, 0.73978853, 0.60376877],
                            (err: BusinessError, data: Array<number>) => {
  if (err) {
    console.error(`Failed to register data. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  for (let i = 0; i < data.length; i++) {
    console.info("Succeeded in getting data[" + i + "]: " + data[i]);
  }
})
```

## sensor.createRotationMatrix<sup>(deprecated)</sup>

createRotationMatrix(rotationVector: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

将旋转矢量转换为旋转矩阵，使用Promise异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getRotationMatrix](#sensorgetrotationmatrix9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名            | 类型                  | 必填   | 说明      |
| -------------- | ------------------- | ---- | ------- |
| rotationVector | Array&lt;number&gt; | 是    | 表示旋转矢量。 |

**返回值**：

| 类型                               | 说明                       |
| ---------------------------------- | -------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | 使用异步方式返回旋转矩阵。 |

**示例**：

 ```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createRotationMatrix([0.20046076, 0.21907, 0.73978853, 0.60376877]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting createRotationMatrix_promise');
  for (let i = 0; i < data.length; i++) {
    console.info("data[" + i + "]: " + data[i]);
  }
}).catch((reason: BusinessError) => {
  console.info("Succeeded in getting promise::catch", reason);
})
 ```

## sensor.createQuaternion<sup>(deprecated)</sup>

createQuaternion(rotationVector: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

将旋转矢量转换为四元数，使用Callback异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getQuaternion](#sensorgetquaternion9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名         | 类型                                     | 必填 | 说明             |
| -------------- | ---------------------------------------- | ---- | ---------------- |
| rotationVector | Array&lt;number&gt;                      | 是   | 表示旋转矢量。   |
| callback       | AsyncCallback&lt;Array&lt;number&gt;&gt; | 是   | 异步返回四元数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.createQuaternion([0.20046076, 0.21907, 0.73978853, 0.60376877],
                        (err: BusinessError, data: Array<number>) => {
  if (err) {
    console.error(`Failed to register data. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  for (let i = 0; i < data.length; i++) {
    console.info("Succeeded in getting data[" + i + "]: " + data[i]);
  }
})
```

## sensor.createQuaternion<sup>(deprecated)</sup>

createQuaternion(rotationVector: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

将旋转矢量转换为四元数，使用Promise异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getQuaternion](#sensorgetquaternion9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名            | 类型                  | 必填   | 说明      |
| -------------- | ------------------- | ---- | ------- |
| rotationVector | Array&lt;number&gt; | 是    | 表示旋转矢量。 |

**返回值**：

| 类型                               | 说明                     |
| ---------------------------------- | ------------------------ |
| Promise&lt;Array&lt;number&gt;&gt; | 使用异步方式返回四元数。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createQuaternion([0.20046076, 0.21907, 0.73978853, 0.60376877]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting createQuaternion_promise');
  for (let i = 0; i < data.length; i++) {
    console.info("data[" + i + "]: " + data[i]);
  }
}).catch((err: BusinessError) => {
  console.info(`Failed to get promise.`);
})
```

## sensor.getDirection<sup>(deprecated)</sup>

getDirection(rotationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

根据旋转矩阵计算设备的方向，使用Callback异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getOrientation](#sensorgetorientation9)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名         | 类型                                     | 必填 | 说明                                  |
| -------------- | ---------------------------------------- | ---- | ------------------------------------- |
| rotationMatrix | Array&lt;number&gt;                      | 是   | 表示旋转矩阵。                        |
| callback       | AsyncCallback&lt;Array&lt;number&gt;&gt; | 是   | 异步返回围绕z、x、y轴方向的旋转角度。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.getDirection([1, 0, 0, 0, 1, 0, 0, 0, 1], (err: BusinessError, data: Array<number>) => {
  if (err) {
    console.error(`Failed to register data. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info("Succeeded in getting getDirection interface get data: " + data);
  for (let i = 1; i < data.length; i++) {
    console.info("Succeeded in getting sensor_getDirection_callback" + data[i]);
  }
})
```

## sensor.getDirection<sup>(deprecated)</sup>

getDirection(rotationMatrix: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

根据旋转矩阵计算设备的方向，使用Promise异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getOrientation](#sensorgetorientation9-1)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名            | 类型                  | 必填   | 说明      |
| -------------- | ------------------- | ---- | ------- |
| rotationMatrix | Array&lt;number&gt; | 是    | 表示旋转矩阵。 |

**返回值**：

| 类型                               | 说明                                          |
| ---------------------------------- | --------------------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | 使用异步方式返回围绕z、x、y轴方向的旋转角度。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getDirection([1, 0, 0, 0, 1, 0, 0, 0, 1]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting sensor_getAltitude_Promise', data);
  for (let i = 1; i < data.length; i++) {
    console.info("Succeeded in getting sensor_getDirection_promise" + data[i]);
  }
}).catch((err: BusinessError) => {
  console.info(`Failed to get promise.`);
})
```

## sensor.createRotationMatrix<sup>(deprecated)</sup>

createRotationMatrix(gravity: Array&lt;number&gt;, geomagnetic: Array&lt;number&gt;, callback: AsyncCallback&lt;RotationMatrixResponse&gt;): void

根据重力矢量和地磁矢量计算旋转矩阵，使用Callback异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getRotationMatrix](#sensorgetrotationmatrix9-2)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名      | 类型                                                         | 必填 | 说明               |
| ----------- | ------------------------------------------------------------ | ---- | ------------------ |
| gravity     | Array&lt;number&gt;                                          | 是   | 表示重力向量。     |
| geomagnetic | Array&lt;number&gt;                                          | 是   | 表示地磁矢量。     |
| callback    | AsyncCallback&lt;[RotationMatrixResponse](#rotationmatrixresponse)&gt; | 是   | 异步返回旋转矩阵。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.createRotationMatrix([-0.27775216, 0.5351276, 9.788099], [210.87253, -78.6096, -111.44444], 
                            (err: BusinessError, data: sensor.RotationMatrixResponse) => {
  if (err) {
    console.error(`Failed to get create rotationMatrix. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(JSON.stringify(data));
})
```

## sensor.createRotationMatrix<sup>(deprecated)</sup>

createRotationMatrix(gravity: Array&lt;number&gt;, geomagnetic: Array&lt;number&gt;): Promise&lt;RotationMatrixResponse&gt;

根据重力矢量和地磁矢量计算旋转矩阵，使用Promise异步方式返回结果。

> **说明**：
>
> 从API version 9 开始不再维护，建议使用[sensor.getRotationMatrix](#sensorgetrotationmatrix9-3)<sup>9+</sup>代替。

**系统能力**：SystemCapability.Sensors.Sensor

**参数**：

| 参数名         | 类型                  | 必填   | 说明      |
| ----------- | ------------------- | ---- | ------- |
| gravity     | Array&lt;number&gt; | 是    | 表示重力向量。 |
| geomagnetic | Array&lt;number&gt; | 是    | 表示地磁矢量。 |

**返回值**：

| 类型                                                         | 说明                       |
| ------------------------------------------------------------ | -------------------------- |
| Promise&lt;[RotationMatrixResponse](#rotationmatrixresponse)&gt; | 使用异步方式返回旋转矩阵。 |

**示例**：

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createRotationMatrix([-0.27775216, 0.5351276, 9.788099], [210.87253, -78.6096, -111.44444]);
promise.then((data: sensor.RotationMatrixResponse) => {
  console.info(JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.info(`Failed to get promise.`);
})
```
