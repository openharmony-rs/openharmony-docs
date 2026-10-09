# @ohos.sensor (Sensor)
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @LiuChao-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->

The **@ohos.sensor** module is a sensor service module provided by HarmonyOS in Sensor Service Kit. This module provides unified APIs to access sensor data, including data subscription, query, and algorithm calculation for various physical sensors on the device.

The **sensor** module provides unified APIs to access sensor data, including data subscription, query, and algorithm calculation for various physical sensors on the device.

Use this module to subscribe to sensor data when your app needs to detect the device motion status (such as shake and flip), detect environmental conditions (such as automatic screen brightness adjustment and atmospheric pressure measurement for altitude estimation), obtain the device orientation (such as compass navigation), or monitor health data (such as heart rate and step count). When mathematical transformation and calculation of sensor data are required, use the sensor algorithm APIs.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version. Before subscribing to sensor data, call [getSingleSensor](#sensorgetsinglesensor9) to obtain the target sensor. For details about how to use the API, see [Sensor Development](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/sensor-guidelines#how-to-develop). If any error occurs, see the error code description of the API. When you subscribe to the sensor data, ensure that the **on** and **off** APIs are used in pairs.

The **sensor** module provides APIs for subscribing to and querying sensor data. The core process is as follows:

1. Use [sensor.getSingleSensor](#sensorgetsinglesensor9) or [sensor.getSensorListSync](#sensorgetsensorlistsync12) to query sensor information and ensure that the device supports the target sensor.
2. Use **sensor.on** to subscribe to sensor data and continuously receive data callbacks.
3. Use **sensor.once** to obtain sensor data once, which is suitable for scenarios where continuous listening is not required.
4. Use **sensor.off** to cancel the subscription. Ensure that **on** and **off** are called in pairs.

Differences between **sensor.on** and **sensor.once** are as follows:

- **sensor.on** continuously subscribes to sensor data and repeatedly reports the data through the callback. It is suitable for scenarios that require real-time monitoring.
- **sensor.once** obtains sensor data only once. The callback is triggered only once, and the subscription is automatically canceled. It is suitable for scenarios where data needs to be collected only once.

Note:

- Before subscribing to a sensor, you are advised to use **getSingleSensor** to check whether the device supports the sensor.
- The **on** API for subscription and the **off** API for cancellation must be used in pairs to avoid resource leak.
- For sensors that require permissions (such as the accelerometer, gyroscope, heart rate sensor, and pedometer), you must request the corresponding permissions first.

## Modules to Import

```ts
import { sensor } from '@kit.SensorServiceKit';
```

## sensor.on('SensorId.ACCELEROMETER')<sup>9+</sup>

on(type: SensorId.ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;, options?: Options): void

Subscribes to data of the acceleration sensor. This API uses an asynchronous callback to return the result. The acceleration sensor measures the acceleration of the device along the x, y, and z axes, including the gravity acceleration component. This sensor is applicable to scenarios where the device motion status needs to be detected, such as screen rotation, game control, and step counting. After this method is called, the system continuously reports acceleration data at the specified frequency through the callback.

**Required permissions**: ohos.permission.ACCELEROMETER

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).ACCELEROMETER                         | Yes  | Sensor type. The value is fixed at **SensorId.ACCELEROMETER**.             |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | Yes  | Callback used to report the sensor data, which is an **AccelerometerResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to acceleration sensor data.
  sensor.on(sensor.SensorId.ACCELEROMETER, (data: sensor.AccelerometerResponse) => {
    // Output the X, Y, and Z coordinate components.
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

## sensor.on('SensorId.FUSION_PRESSURE')<sup>22+</sup>

on(type: SensorId.FUSION_PRESSURE, callback: Callback&lt;FusionPressureResponse&gt;, options?: Options): void

Subscribes to the fused pressure sensor data. This API uses an asynchronous callback to return the result. The fused pressure sensor is used to obtain pressure data processed by the fusion algorithm. It applies only to smart watches. This is applicable to health monitoring scenarios where wrist pressure data needs to be obtained. After this method is called, the system continuously reports acceleration data at the specified frequency through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).FUSION_PRESSURE            | Yes  | Sensor type. The value is fixed at SensorId.FUSION_PRESSURE.|
| callback | Callback&lt;[FusionPressureResponse](#fusionpressureresponse22)&gt; | Yes  | Callback used to report the sensor data, which is a **FusionPressureResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to the fusion pressure sensor data.
  sensor.on(sensor.SensorId.FUSION_PRESSURE, (data: sensor.FusionPressureResponse) => {
    // Output the fused pressure value.
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

## sensor.on('SensorId.ACCELEROMETER_UNCALIBRATED')<sup>9+</sup>

on(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback&lt;AccelerometerUncalibratedResponse&gt;, options?: Options): void

Subscribes to data of the uncalibrated acceleration sensor. This API uses an asynchronous callback to return the result. The difference between the uncalibrated acceleration sensor and the acceleration sensor is that the **biasX**, **biasY**, and **biasZ** values reported by the uncalibrated acceleration sensor are not calibrated by the system. This sensor is suitable for scenarios where raw acceleration data is required or a custom calibration algorithm is implemented. Compared with **sensor.on('SensorId.ACCELEROMETER')**, this API provides additional bias information, which is suitable for scenarios where device calibration bias needs to be analyzed.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ACCELEROMETER_UNCALIBRATED            | Yes  | Sensor type. The value is fixed at **SensorId.ACCELEROMETER_UNCALIBRATED**. |
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | Yes  | Callback used to report the sensor data, which is an **AccelerometerUncalibratedResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to uncalibrated acceleration sensor data.
  sensor.on(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, (data: sensor.AccelerometerUncalibratedResponse) => {
    // Output the X, Y, and Z coordinate components and offset values.
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

## sensor.on('SensorId.AMBIENT_LIGHT')<sup>9+</sup>

on(type: SensorId.AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;, options?: Options): void

Subscribes to data of the ambient light sensor. This API uses an asynchronous callback to return the result. The ambient light sensor is used to measure the light intensity of the surrounding environment. It is applicable to scenarios such as automatic screen brightness adjustment and determining the brightness of the environment. After this method is called, the system continuously reports ambient light intensity data at the specified frequency through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                           | Mandatory| Description                                                       |
| -------- | ----------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).AMBIENT_LIGHT            | Yes  | Sensor type. The value is fixed at **SensorId.AMBIENT_LIGHT**.             |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **LightResponse** object.        |
| options  | [Options](#options)                             | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to ambient light sensor data.
  sensor.on(sensor.SensorId.AMBIENT_LIGHT, (data: sensor.LightResponse) => {
    // Output the ambient light intensity.
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

## sensor.on('SensorId.AMBIENT_TEMPERATURE')<sup>9+</sup>

on(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback&lt;AmbientTemperatureResponse&gt;, options?: Options): void

Subscribes to data of the ambient temperature sensor. This API uses an asynchronous callback to return the result. The temperature sensor is used to measure the ambient temperature around the device. It is applicable to scenarios such as ambient temperature monitoring and temperature compensation. After this method is called, the system continuously reports temperature data at the specified frequency through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).AMBIENT_TEMPERATURE                   | Yes  | Sensor type. The value is fixed at **SensorId.AMBIENT_TEMPERATURE**.        |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | Yes  | Callback used to report the sensor data, which is an **AmbientTemperatureResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the ambient temperature sensor.
  sensor.on(sensor.SensorId.AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
    // Output the temperature value.
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

## sensor.on('SensorId.BAROMETER')<sup>9+</sup>

on(type: SensorId.BAROMETER, callback: Callback&lt;BarometerResponse&gt;, options?: Options): void

Subscribes to data of the barometer sensor. This API uses an asynchronous callback to return the result. The barometric pressure sensor is used to measure atmospheric pressure. It is applicable to scenarios such as altitude estimation and weather forecast assistance. After this method is called, the system continuously reports barometric pressure data at the specified frequency through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).BAROMETER                        | Yes  | Sensor type. The value is fixed at **SensorId.BAROMETER**.                 |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **BarometerResponse** object.    |
| options  | [Options](#options)                                     | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the barometer sensor.
  sensor.on(sensor.SensorId.BAROMETER, (data: sensor.BarometerResponse) => {
    // Output the atmospheric pressure value.
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

## sensor.on('SensorId.GRAVITY')<sup>9+</sup>

on(type: SensorId.GRAVITY, callback: Callback&lt;GravityResponse&gt;, options?: Options): void

Subscribes to data of the gravity sensor. This API uses an asynchronous callback to return the result. The gravity sensor measures the gravity acceleration components of the device along the x, y, and z axes. It is applicable to scenarios where the gravity component needs to be separated for motion analysis, such as game control and motion detection. After this method is called, the system continuously reports gravity component data at the specified frequency through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                               | Mandatory| Description                                                       |
| -------- | --------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).GRAVITY                      | Yes  | Sensor type. The value is fixed at **SensorId.GRAVITY**.                   |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **GravityResponse** object.      |
| options  | [Options](#options)                                 | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the gravity sensor.
  sensor.on(sensor.SensorId.GRAVITY, (data: sensor.GravityResponse) => {
    // Output the X, Y, and Z coordinate components.
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

## sensor.on('SensorId.GYROSCOPE')<sup>9+</sup>

on(type: SensorId.GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;, options?: Options): void

Subscribes to data of the gyroscope sensor. This API uses an asynchronous callback to return the result. The gyroscope sensor is used to measure the angular velocity of a device around the x, y, and z axes. It is applicable to scenarios such as device rotation detection, posture tracking, and game control. After this method is called, the system continuously reports angular velocity data at the specified frequency through the callback.

**Required permissions**: ohos.permission.GYROSCOPE

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).GYROSCOPE                        | Yes  | Sensor type. The value is fixed at **SensorId.GYROSCOPE**.                 |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt; | Yes  | Callback used to report the sensor data, which is a **GyroscopeResponse** object.    |
| options  | [Options](#options)                                     | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the calibrated gyroscope sensor.
  sensor.on(sensor.SensorId.GYROSCOPE, (data: sensor.GyroscopeResponse) => {
    // Output the X, Y, and Z coordinate components.
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

## sensor.on('SensorId.GYROSCOPE_UNCALIBRATED')<sup>9+</sup>

on(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback&lt;GyroscopeUncalibratedResponse&gt;, options?: Options): void

Subscribes to data of the uncalibrated gyroscope sensor. This API uses an asynchronous callback to return the result. The difference between the uncalibrated gyroscope sensor and the gyroscope sensor is that the **biasX**, **biasY**, and **biasZ** values reported by the uncalibrated gyroscope sensor are not calibrated by the system. This sensor is suitable for scenarios where raw gyroscope data is required or where the calibration algorithm needs to be implemented by the app. Compared with **sensor.on('SensorId.GYROSCOPE')**, this API additionally provides bias information, which is suitable for scenarios where the gyroscope calibration bias needs to be analyzed.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor 

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).GYROSCOPE_UNCALIBRATED                | Yes  | Sensor type. The value is fixed at **SensorId.GYROSCOPE_UNCALIBRATED**.     |
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **GyroscopeUncalibratedResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the uncalibrated gyroscope sensor.
  sensor.on(sensor.SensorId.GYROSCOPE_UNCALIBRATED, (data: sensor.GyroscopeUncalibratedResponse) => {
    // Output the X, Y, and Z coordinate components and offset values.
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

## sensor.on('SensorId.HALL')<sup>9+</sup>

on(type: SensorId.HALL, callback: Callback&lt;HallResponse&gt;, options?: Options): void

Subscribes to data of the Hall effect sensor. This API uses an asynchronous callback to return the result. The Hall effect sensor is used to detect magnetic field changes, and is often used to detect the opening and closing status of a flip phone or leather case. When Hall effect events are frequently triggered, you can use the **options** parameter to set the data reporting frequency. After this method is called, the system continuously reports Hall effect sensor data through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                         | Mandatory| Description                                                        |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).HALL                   | Yes  | Sensor type. The value is fixed at **SensorId.HALL**.                       |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **HallResponse** object.          |
| options  | [Options](#options)                           | No  | Optional parameters used to set the reporting frequency of the sensor when the Hall effect sensor is frequently triggered. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the Hall effect sensor.
  sensor.on(sensor.SensorId.HALL, (data: sensor.HallResponse) => {
    // Output the Hall effect sensor status.
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

## sensor.on('SensorId.HEART_RATE')<sup>9+</sup>

on(type: SensorId.HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;, options?: Options): void

Subscribes to data of the heart rate sensor. This API uses an asynchronous callback to return the result. The heart rate sensor is used to measure the heart rate of a user. It is applicable to scenarios such as health monitoring and exercise assistance. After this method is called, the system continuously reports heart rate data at the specified frequency through the callback.

**Required permissions**: ohos.permission.READ_HEALTH_DATA

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).HEART_RATE                       | Yes  | Sensor type. The value is fixed at **SensorId.HEART_RATE**.                |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **HeartRateResponse** object.    |
| options  | [Options](#options)                                     | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to heart rate sensor data.
  sensor.on(sensor.SensorId.HEART_RATE, (data: sensor.HeartRateResponse) => {
    // Output the heart rate value.
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

## sensor.on('SensorId.HUMIDITY')<sup>9+</sup>

on(type: SensorId.HUMIDITY, callback: Callback&lt;HumidityResponse&gt;, options?: Options): void

Subscribes to data of the humidity sensor. This API uses an asynchronous callback to return the result. The humidity sensor is used to measure the relative humidity of the surrounding environment. It is applicable to scenarios such as ambient humidity monitoring and collaboration with other smart home devices. After this method is called, the system continuously reports humidity data at the specified frequency through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                       |
| -------- | ----------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).HUMIDITY                       | Yes  | Sensor type. The value is fixed at **SensorId.HUMIDITY**.                  |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **HumidityResponse** object.     |
| options  | [Options](#options)                                   | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to humidity sensor data.
  sensor.on(sensor.SensorId.HUMIDITY, (data: sensor.HumidityResponse) => {
    // Output the humidity value.
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

## sensor.on('SensorId.LINEAR_ACCELEROMETER')<sup>9+</sup>

on(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback&lt;LinearAccelerometerResponse&gt;, options?: Options): void

Subscribes to data of the linear acceleration sensor. This API uses an asynchronous callback to return the result. The linear acceleration sensor measures the acceleration (excluding the gravity component) of the device along the x, y, and z axes. It is applicable to scenarios where the pure motion acceleration of the device needs to be sensed, such as motion tracking and collision detection. Compared with **sensor.on('SensorId.ACCELEROMETER')**, this API does not contain the gravity component and is applicable to scenarios where only the device's motion acceleration is required.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).LINEAR_ACCELEROMETER                  | Yes  | Sensor type. The value is fixed at **SensorId.LINEAR_ACCELEROMETER**.       |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **LinearAccelerometerResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the linear acceleration sensor.
  sensor.on(sensor.SensorId.LINEAR_ACCELEROMETER, (data: sensor.LinearAccelerometerResponse) => {
    // Output the X, Y, and Z coordinate components.
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

## sensor.on('SensorId.MAGNETIC_FIELD')<sup>9+</sup>

on(type: SensorId.MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;, options?: Options): void

Subscribes to data of the magnetic field sensor. This API uses an asynchronous callback to return the result. The magnetic field sensor is used to measure the magnetic field strength around the device in the x, y, and z axes. It is applicable to scenarios such as compass, direction detection, and metal detection. After this method is called, the system continuously reports magnetic field component data at the specified frequency through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD                        | Yes  | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD**.            |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **MagneticFieldResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the magnetic field sensor.
  sensor.on(sensor.SensorId.MAGNETIC_FIELD, (data: sensor.MagneticFieldResponse) => {
    // Output the X, Y, and Z coordinate components.
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

## sensor.on('SensorId.MAGNETIC_FIELD_UNCALIBRATED')<sup>9+</sup>

on(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;, options?: Options): void

Subscribes to data of the uncalibrated magnetic field sensor. This API uses an asynchronous callback to return the result. The difference between the uncalibrated magnetic field sensor and the magnetic field sensor is that the **biasX**, **biasY**, and **biasZ** values reported by the uncalibrated magnetic field sensor are not calibrated by the system. This sensor is suitable for scenarios where raw magnetic field data is required or a custom calibration algorithm is implemented. Compared with **sensor.on('SensorId.MAGNETIC_FIELD')**, this API provides the bias information, which is suitable for scenarios where the geomagnetic calibration deviation of the device needs to be analyzed.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD_UNCALIBRATED           | Yes  | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD_UNCALIBRATED**.|
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **MagneticFieldUncalibratedResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the uncalibrated magnetic field sensor.
  sensor.on(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, (data: sensor.MagneticFieldUncalibratedResponse) => {
    // Output the X, Y, and Z coordinate components and offset values.
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

## sensor.on('SensorId.ORIENTATION')<sup>9+</sup>

on(type: SensorId.ORIENTATION, callback: Callback&lt;OrientationResponse&gt;, options?: Options): void

Subscribes to data of the orientation sensor. This API uses an asynchronous callback to return the result. The orientation sensor measures the angles of rotation around the Z-axis (alpha), X-axis (beta), and Y-axis (gamma). It is applicable to scenarios such as screen rotation, compass, and posture sensing. After this method is called, the system continuously reports orientation data at the specified frequency through the callback. Applications or services invoking this API can prompt users to use figure-8 calibration to improve the accuracy of the direction sensor. The sensor has a theoretical error of ±5 degrees, but the specific precision may vary depending on different driver implementations and algorithmic designs.

> **NOTE**
> 
> Applications or services invoking this API can prompt users to use figure-8 calibration to improve the accuracy of the direction sensor. The sensor has a theoretical error of ±5 degrees, but the specific precision may vary depending on different driver implementations and algorithmic designs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                                       |
| -------- | ----------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).ORIENTATION                          | Yes  | Sensor type. The value is fixed at **SensorId.ORIENTATION**.               |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **OrientationResponse** object.  |
| options  | [Options](#options)                                         | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the orientation sensor.
  sensor.on(sensor.SensorId.ORIENTATION, (data: sensor.OrientationResponse) => {
    // Output the angles at which the device rotates around the Z, X, and Y axes.
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

## sensor.on('SensorId.PEDOMETER')<sup>9+</sup>

on(type: SensorId.PEDOMETER, callback: Callback&lt;PedometerResponse&gt;, options?: Options): void

Subscribes to data of the pedometer sensor. This API uses an asynchronous callback to return the result. The pedometer sensor is used to count the number of steps taken by a user. It is applicable to scenarios such as fitness tracking and health management. The step counter sensor's data reporting is subject to some delay, and the delay is determined by specific product implementations. After this method is called, the system continuously reports step count data at the specified frequency through the callback.

> **NOTE**
> 
> The pedometer sensor data is reset only when the device is rebooted, not on a daily basis. The step count reported before the reboot is the accumulated value.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).PEDOMETER                        | Yes  | Sensor type. The value is fixed at **SensorId.PEDOMETER**.                 |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **PedometerResponse** object.    |
| options  | [Options](#options)                                     | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the pedometer sensor.
  sensor.on(sensor.SensorId.PEDOMETER, (data: sensor.PedometerResponse) => {
    // Output the step count.
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

## sensor.on('SensorId.PEDOMETER_DETECTION')<sup>9+</sup>

on(type: SensorId.PEDOMETER_DETECTION, callback: Callback&lt;PedometerDetectionResponse&gt;, options?: Options): void

Subscribes to data of the pedometer detection sensor. This API uses an asynchronous callback to return the result. The pedometer detection sensor is used to detect whether a step event (such as a step) occurs. It is applicable to scenarios where the walking status needs to be detected in real time. Compared with **sensor.on('SensorId.PEDOMETER')**, this API reports the scalar value of a step event instead of the accumulated step count. It is applicable to scenarios where single-step events need to be detected.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PEDOMETER_DETECTION                   | Yes  | Sensor type. The value is fixed at **SensorId.PEDOMETER_DETECTION**.        |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **PedometerDetectionResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the pedometer detection sensor.
  sensor.on(sensor.SensorId.PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
    // Output the scalar value of the step count.
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

## sensor.on('SensorId.PROXIMITY')<sup>9+</sup>

on(type: SensorId.PROXIMITY, callback: Callback&lt;ProximityResponse&gt;, options?: Options): void

Subscribes to data of the proximity sensor. This API uses an asynchronous callback to return the result. The proximity sensor is used to detect the distance between an object and the device. It is often used to automatically turn off the screen during a call to prevent accidental touches. When proximity sensor events are frequently triggered, you can use the **options** parameter to set the event reporting frequency. After this method is called, the system continuously reports proximity sensor data through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PROXIMITY                        | Yes  | Sensor type. The value is fixed at **SensorId.PROXIMITY**.                  |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **ProximityResponse** object.     |
| options  | [Options](#options)                                     | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). This parameter is used to set the data reporting frequency when proximity events are frequently triggered.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3.Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Subscribe to data of the proximity sensor.
  sensor.on(sensor.SensorId.PROXIMITY, (data: sensor.ProximityResponse) => {
    // Output the distance value.
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

## sensor.on('SensorId.ROTATION_VECTOR')<sup>9+</sup>

on(type: SensorId.ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;, options?: Options): void

Subscribes to data of the rotation vector sensor. This API uses an asynchronous callback to return the result. The rotation vector sensor is used to indicate the orientation of a device. The data consists of the X, Y, and Z components and the scalar W, and can be used for device orientation estimation and AR/VR scenarios. After this method is called, the system continuously reports rotation vector data at the specified frequency through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ROTATION_VECTOR                       | Yes  | Sensor type. The value is fixed at **SensorId.ROTATION_VECTOR**.            |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **RotationVectorResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3.Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.on('SensorId.SIGNIFICANT_MOTION')<sup>9+</sup>

on(type: SensorId.SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;, options?: Options): void

Subscribes to significant motion sensor data to detect significant motion events such as picking up the device, obvious movement, or violent shaking. This API uses an asynchronous callback to return the result. This API is applicable to scenarios where the device needs to be woken up, an app needs to be started, or the mode needs to be switched based on the user's activity state. After this method is called, the system continuously reports significant motion event data through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).SIGNIFICANT_MOTION                    | Yes  | Sensor type. The value is fixed at **SensorId.SIGNIFICANT_MOTION**.         |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **SignificantMotionResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3.Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.on('SensorId.WEAR_DETECTION')<sup>9+</sup>

on(type: SensorId.WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;, options?: Options): void

Subscribes to data of the wear detection sensor. This API uses an asynchronous callback to return the result. The wear detection sensor is used to detect whether a wearable device, such as a smart watch, is being worn by a user, so that the device can automatically switch its working mode. After this method is called, the system continuously reports wear detection data at the specified frequency through the callback.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).WEAR_DETECTION                        | Yes  | Sensor type. The value is fixed at **SensorId.WEAR_DETECTION**.                         |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **WearDetectionResponse** object.|
| options  | [Options](#options)                                          | No  | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3.Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.on('sensorStatusChange')<sup>19+</sup>

on(type: 'sensorStatusChange', callback: Callback&lt;SensorStatusEvent&gt;): void

Listens for sensor status changes. This API uses an asynchronous callback to return the result. This API is applicable to scenarios where sensor status changes need to be detected, for example, when a remote sensor is connected or disconnected, the sensor list or subscription status needs to be automatically updated.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | string         | Yes  | Event type. The value **sensorStatusChange** indicates the sensor status change event.            |
| callback | Callback&lt;[SensorStatusEvent](#sensorstatusevent19)&gt; | Yes  | Callback used to return the sensor status change event.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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



## sensor.once('SensorId.ACCELEROMETER')<sup>9+</sup>

once(type: SensorId.ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;): void

Obtains data of the acceleration sensor once. This method applies to scenarios where the current acceleration data needs to be obtained only once and continuous listening is not required. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).ACCELEROMETER                         | Yes  | Sensor type. The value is fixed at **SensorId.ACCELEROMETER**.             |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | Yes  | Callback used to report the sensor data, which is an **AccelerometerResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.once('SensorId.ACCELEROMETER_UNCALIBRATED')<sup>9+</sup>

once(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

Obtains data of the uncalibrated acceleration sensor once. This method applies to scenarios where the raw acceleration and offset data needs to be obtained only once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ACCELEROMETER_UNCALIBRATED            | Yes  | Sensor type. The value is fixed at **SensorId.ACCELEROMETER_UNCALIBRATED**. |
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | Yes  | Callback used to report the sensor data, which is an **AccelerometerUncalibratedResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.once('SensorId.AMBIENT_LIGHT')<sup>9+</sup>

once(type: SensorId.AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;): void

Obtains data of the ambient light sensor once. This method applies to scenarios where the current ambient light intensity needs to be obtained only once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                           | Mandatory| Description                                               |
| -------- | ----------------------------------------------- | ---- | --------------------------------------------------- |
| type     | [SensorId](#sensorid9).AMBIENT_LIGHT            | Yes  | Sensor type. The value is fixed at **SensorId.AMBIENT_LIGHT**.     |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **LightResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.once(sensor.SensorId.AMBIENT_LIGHT, (data: sensor.LightResponse) => {
    console.info('Succeeded in invoking once. the ambient light intensity: ' + data.intensity);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once('SensorId.AMBIENT_TEMPERATURE')<sup>9+</sup>

once(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback&lt;AmbientTemperatureResponse&gt;): void

Obtains data of the temperature sensor once. This method applies to scenarios where the current ambient temperature needs to be obtained only once. After the API is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).AMBIENT_TEMPERATURE                   | Yes  | Sensor type. The value is fixed at **SensorId.AMBIENT_TEMPERATURE**.        |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | Yes  | Callback used to report the sensor data, which is an **AmbientTemperatureResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.once(sensor.SensorId.AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
    console.info('Succeeded in invoking once. Temperature: ' + data.temperature);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once('SensorId.BAROMETER')<sup>9+</sup>

once(type: SensorId.BAROMETER, callback: Callback&lt;BarometerResponse&gt;): void

Obtains data of the barometer sensor once. This method applies to scenarios where only the current atmospheric pressure value needs to be obtained once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                   |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| type     | [SensorId](#sensorid9).BAROMETER                        | Yes  | Sensor type. The value is fixed at **SensorId.BAROMETER**.             |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **BarometerResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.once(sensor.SensorId.BAROMETER, (data: sensor.BarometerResponse) => {
    console.info('Succeeded in invoking once. Atmospheric pressure: ' + data.pressure);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once('SensorId.GRAVITY')<sup>9+</sup>

once(type: SensorId.GRAVITY, callback: Callback&lt;GravityResponse&gt;): void

Obtains data of the gravity sensor once. This method applies to the scenario where only the current gravity component needs to be obtained once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                               | Mandatory| Description                                                 |
| -------- | --------------------------------------------------- | ---- | ----------------------------------------------------- |
| type     | [SensorId](#sensorid9).GRAVITY                      | Yes  | Sensor type. The value is fixed at **SensorId.GRAVITY**.             |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **GravityResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.once('SensorId.GYROSCOPE')<sup>9+</sup>

once(type: SensorId.GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;): void

Obtains data of the gyroscope sensor once. This method applies to scenarios where only the current angular velocity needs to be obtained once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                   |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| type     | [SensorId](#sensorid9).GYROSCOPE                        | Yes  | Sensor type. The value is fixed at **SensorId.GYROSCOPE**.             |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt; | Yes  | Callback used to report the sensor data, which is a **GyroscopeResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.once('SensorId.GYROSCOPE_UNCALIBRATED')<sup>9+</sup>

once(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

Obtains data of the uncalibrated gyroscope sensor once. This method applies to scenarios where the raw angular velocity and offset data needs to be obtained only once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).GYROSCOPE_UNCALIBRATED                | Yes  | Sensor type. The value is fixed at **SensorId.GYROSCOPE_UNCALIBRATED**.     |
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **GyroscopeUncalibratedResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.once('SensorId.HALL')<sup>9+</sup>

once(type: SensorId.HALL, callback: Callback&lt;HallResponse&gt;): void

Obtains data of the Hall effect sensor once. This method applies to scenarios where the current Hall effect status needs to be detected only once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                         | Mandatory| Description                                              |
| -------- | --------------------------------------------- | ---- | -------------------------------------------------- |
| type     | [SensorId](#sensorid9).HALL                   | Yes  | Sensor type. The value is fixed at **SensorId.HALL**.             |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **HallResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.once(sensor.SensorId.HALL, (data: sensor.HallResponse) => {
    console.info('Succeeded in invoking once. Status: ' + data.status);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once('SensorId.HEART_RATE')<sup>9+</sup>

once(type: SensorId.HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;): void

Obtains data of the heart rate sensor once. This method applies to scenarios where only the current heart rate needs to be obtained once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**Required permissions**: ohos.permission.READ_HEALTH_DATA

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                   |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| type     | [SensorId](#sensorid9).HEART_RATE                       | Yes  | Sensor type. The value is fixed at **SensorId.HEART_RATE**.            |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **HeartRateResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.once(sensor.SensorId.HEART_RATE, (data: sensor.HeartRateResponse) => {
    console.info('Succeeded in invoking once. Heart rate: ' + data.heartRate);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once('SensorId.HUMIDITY')<sup>9+</sup>

once(type: SensorId.HUMIDITY, callback: Callback&lt;HumidityResponse&gt;): void

Obtains data of the humidity sensor once. This method applies to the scenario where the current humidity needs to be obtained only once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                  |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------ |
| type     | [SensorId](#sensorid9).HUMIDITY                       | Yes  | Sensor type. The value is fixed at **SensorId.HUMIDITY**.             |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **HumidityResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.once(sensor.SensorId.HUMIDITY, (data: sensor.HumidityResponse) => {
    console.info('Succeeded in invoking once. Humidity: ' + data.humidity);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once('SensorId.LINEAR_ACCELEROMETER')<sup>9+</sup>

once(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback&lt;LinearAccelerometerResponse&gt;): void

Obtains data of the linear acceleration sensor once. This method applies to scenarios where only the current linear acceleration (excluding the gravity component) needs to be obtained once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).LINEAR_ACCELEROMETER                  | Yes  | Sensor type. The value is fixed at **SensorId.LINEAR_ACCELEROMETER**.       |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **LinearAccelerometerResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.once('SensorId.MAGNETIC_FIELD')<sup>9+</sup>

once(type: SensorId.MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;): void

Obtains data of the magnetic field sensor once. This method applies to scenarios where only the current magnetic field component needs to be obtained once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD                        | Yes  | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD**.            |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **MagneticFieldResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.once('SensorId.MAGNETIC_FIELD_UNCALIBRATED')<sup>9+</sup>

once(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

Obtains data of the uncalibrated magnetic field sensor once. This method applies to scenarios where the raw magnetic field and offset data needs to be obtained only once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD_UNCALIBRATED           | Yes  | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD_UNCALIBRATED**.|
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **MagneticFieldUncalibratedResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.once('SensorId.ORIENTATION')<sup>9+</sup>

once(type: SensorId.ORIENTATION, callback: Callback&lt;OrientationResponse&gt;): void

Obtains data of the orientation sensor once. This method applies to scenarios where the current device orientation needs to be obtained only once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                                     |
| -------- | ----------------------------------------------------------- | ---- | --------------------------------------------------------- |
| type     | [SensorId](#sensorid9).ORIENTATION                          | Yes  | Sensor type. The value is fixed at **SensorId.ORIENTATION**.             |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **OrientationResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.once('SensorId.PEDOMETER')<sup>9+</sup>

once(type: SensorId.PEDOMETER, callback: Callback&lt;PedometerResponse&gt;): void

Obtains data of the pedometer sensor once. The step counter sensor's data reporting is subject to some delay, and the delay is determined by specific product implementations. This method is applicable to scenarios where only the current step count needs to be obtained once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

> **NOTE**
> 
> The pedometer sensor data is cleared only when the device is rebooted, not on a daily basis. The step count reported before the reboot is the accumulated value.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                   |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| type     | [SensorId](#sensorid9).PEDOMETER                        | Yes  | Sensor type. The value is fixed at **SensorId.PEDOMETER**.             |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **PedometerResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.once(sensor.SensorId.PEDOMETER, (data: sensor.PedometerResponse) => {
    console.info('Succeeded in invoking once. Step count: ' + data.steps);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once('SensorId.PEDOMETER_DETECTION')<sup>9+</sup>

once(type: SensorId.PEDOMETER_DETECTION, callback: Callback&lt;PedometerDetectionResponse&gt;): void

Obtains data of the pedometer sensor once. This method applies to scenarios where only one-time step counting is required. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PEDOMETER_DETECTION                   | Yes  | Sensor type. The value is fixed at **SensorId.PEDOMETER_DETECTION**.        |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **PedometerDetectionResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.once(sensor.SensorId.PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
    console.info('Succeeded in invoking once. Scalar data: ' + data.scalar);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once('SensorId.PROXIMITY')<sup>9+</sup>

once(type: SensorId.PROXIMITY, callback: Callback&lt;ProximityResponse&gt;): void

Obtains data of the proximity sensor once. This method applies to scenarios where detection of the current proximity status is required only once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                   |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------- |
| type     | [SensorId](#sensorid9).PROXIMITY                        | Yes  | Sensor type. The value is fixed at **SensorId.PROXIMITY**.             |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **ProximityResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.once(sensor.SensorId.PROXIMITY, (data: sensor.ProximityResponse) => {
    console.info('Succeeded in invoking once. Distance: ' + data.distance);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once('SensorId.ROTATION_VECTOR')<sup>9+</sup>

once(type: SensorId.ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;): void

Obtains data of the rotation vector sensor once. This method applies to scenarios where the current device posture needs to be obtained only once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ROTATION_VECTOR                       | Yes  | Sensor type. The value is fixed at **SensorId.ROTATION_VECTOR**.            |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **RotationVectorResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.once('SensorId.SIGNIFICANT_MOTION')<sup>9+</sup>

once(type: SensorId.SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;): void

Obtains the significant motion sensor data once. This API applies to scenarios where significant motion needs to be detected only once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).SIGNIFICANT_MOTION                    | Yes  | Sensor type. The value is fixed at **SensorId.SIGNIFICANT_MOTION**.         |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **SignificantMotionResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.once(sensor.SensorId.SIGNIFICANT_MOTION, (data: sensor.SignificantMotionResponse) => {
    console.info('Succeeded in invoking once. Scalar data: ' + data.scalar);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.once('SensorId.WEAR_DETECTION')<sup>9+</sup>

once(type: SensorId.WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;): void

Obtains data of the wear detection sensor once. This API applies to scenarios where the wear status needs to be detected only once. After the method is called, the callback is triggered only once, and the subscription is automatically canceled.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).WEAR_DETECTION                        | Yes  | Sensor type. The value is fixed at [SensorId](#sensorid9).WEAR_DETECTION.            |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | Yes  | Callback used to report the sensor data, which is a **WearDetectionResponse** object.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.once(sensor.SensorId.WEAR_DETECTION, (data: sensor.WearDetectionResponse) => {
    console.info('Succeeded in invoking once. Wear status: ' + data.value);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke once. Code: ${e.code}, message: ${e.message}`);
}
```


## sensor.off('SensorId.ACCELEROMETER')<sup>9+</sup>

off(type: SensorId.ACCELEROMETER, callback?: Callback&lt;AccelerometerResponse&gt;): void

Unsubscribes from data of the acceleration sensor. Call this method to cancel the subscription when you no longer need to receive data from the acceleration sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.ACCELEROMETER

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ACCELEROMETER                         | Yes  | Sensor type. The value is fixed at **SensorId.ACCELEROMETER**.              |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.ACCELEROMETER, callback1);
  sensor.on(sensor.SensorId.ACCELEROMETER, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.ACCELEROMETER, callback1);
  // Unsubscribe from all callbacks of the SensorId.ACCELEROMETER type.
  sensor.off(sensor.SensorId.ACCELEROMETER);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.ACCELEROMETER')<sup>19+</sup>

off(type: SensorId.ACCELEROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;AccelerometerResponse&gt;): void

Unsubscribes from data of the acceleration sensor. Call this method to cancel the subscription when the acceleration sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.ACCELEROMETER

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name               | Type                                                        | Mandatory| Description                                                        |
|--------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type               | [SensorId](#sensorid9).ACCELEROMETER                         | Yes  | Sensor type. The value is fixed at **SensorId.ACCELEROMETER**.              |
| sensorInfoParam    | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback           | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.AccelerometerResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.ACCELEROMETER;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.ACCELEROMETER_UNCALIBRATED')<sup>9+</sup>  

off(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback?: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

Unsubscribes from data of the uncalibrated acceleration sensor. Call this method when you no longer need to receive data of the uncalibrated acceleration sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ACCELEROMETER_UNCALIBRATED            | Yes  | Sensor type. The value is fixed at **SensorId.ACCELEROMETER_UNCALIBRATED**. |
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, callback1);
  sensor.on(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, callback1);
  // Unsubscribe from all callbacks of the SensorId.ACCELEROMETER_UNCALIBRATED type.
  sensor.off(sensor.SensorId.ACCELEROMETER_UNCALIBRATED);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.FUSION_PRESSURE')<sup>22+</sup>

off(type: SensorId.FUSION_PRESSURE, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;FusionPressureResponse&gt;): void

Unsubscribes from the fused pressure sensor data. Call this method to cancel the subscription when the fused pressure sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                        | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).FUSION_PRESSURE            | Yes  | Sensor type. The value is fixed at SensorId.FUSION_PRESSURE. |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[FusionPressureResponse](#fusionpressureresponse22)&gt; | No  | Callback used for unsubscription. If this parameter is not specified, all callbacks of the specified sensor type are unsubscribed from.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.FusionPressureResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.FUSION_PRESSURE;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.ACCELEROMETER_UNCALIBRATED')<sup>19+</sup>

off(type: SensorId.ACCELEROMETER_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

Unsubscribes from data of the uncalibrated acceleration sensor. Call this method when you no longer need to receive data of the uncalibrated acceleration sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                        | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).ACCELEROMETER_UNCALIBRATED            | Yes  | Sensor type. The value is fixed at **SensorId.ACCELEROMETER_UNCALIBRATED**. |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.AccelerometerUncalibratedResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.ACCELEROMETER_UNCALIBRATED;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.AMBIENT_LIGHT')<sup>9+</sup> 

off(type: SensorId.AMBIENT_LIGHT, callback?: Callback&lt;LightResponse&gt;): void

Unsubscribes from data of the ambient light sensor. When the ambient light sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                           | Mandatory| Description                                                        |
| -------- | ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).AMBIENT_LIGHT            | Yes  | Sensor type. The value is fixed at **SensorId.AMBIENT_LIGHT**.              |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.AMBIENT_LIGHT, callback1);
  sensor.on(sensor.SensorId.AMBIENT_LIGHT, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.AMBIENT_LIGHT, callback1);
  // Unsubscribe from all callbacks of the SensorId.AMBIENT_LIGHT type.
  sensor.off(sensor.SensorId.AMBIENT_LIGHT);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.AMBIENT_LIGHT')<sup>19+</sup>

off(type: SensorId.AMBIENT_LIGHT, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;LightResponse&gt;): void

Unsubscribes from data of the ambient light sensor. When the ambient light sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                           | Mandatory| Description                                                        |
|------------------| ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).AMBIENT_LIGHT            | Yes  | Sensor type. The value is fixed at **SensorId.AMBIENT_LIGHT**.              |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[LightResponse](#lightresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.LightResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.AMBIENT_LIGHT;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.AMBIENT_TEMPERATURE')<sup>9+</sup> 

off(type: SensorId.AMBIENT_TEMPERATURE, callback?: Callback&lt;AmbientTemperatureResponse&gt;): void

Unsubscribes from data of the ambient temperature sensor. When the ambient temperature sensor data is no longer needed, call this API to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).AMBIENT_TEMPERATURE                   | Yes  | Sensor type. The value is fixed at **SensorId.AMBIENT_TEMPERATURE**.        |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.AMBIENT_TEMPERATURE, callback1);
  sensor.on(sensor.SensorId.AMBIENT_TEMPERATURE, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.AMBIENT_TEMPERATURE, callback1);
  // Unsubscribe from all callbacks of the SensorId.AMBIENT_TEMPERATURE type.
  sensor.off(sensor.SensorId.AMBIENT_TEMPERATURE);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.AMBIENT_TEMPERATURE')<sup>19+</sup>

off(type: SensorId.AMBIENT_TEMPERATURE, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;AmbientTemperatureResponse&gt;): void

Unsubscribes from data of the ambient temperature sensor. When the ambient temperature sensor data is no longer needed, call this API to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                        | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).AMBIENT_TEMPERATURE                   | Yes  | Sensor type. The value is fixed at **SensorId.AMBIENT_TEMPERATURE**.        |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.AmbientTemperatureResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.AMBIENT_TEMPERATURE;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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


## sensor.off('SensorId.BAROMETER')<sup>9+</sup>  

off(type: SensorId.BAROMETER, callback?: Callback&lt;BarometerResponse&gt;): void

Unsubscribes from data of the barometer sensor. Call this method to cancel the subscription when the barometric pressure sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).BAROMETER                        | Yes  | Sensor type. The value is fixed at **SensorId.BAROMETER**.                  |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
    console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
    console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
    sensor.on(sensor.SensorId.BAROMETER, callback1);
    sensor.on(sensor.SensorId.BAROMETER, callback2);
    // Unsubscribe from callback1.
    sensor.off(sensor.SensorId.BAROMETER, callback1);
    // Unsubscribe from all callbacks of the SensorId.BAROMETER type.
    sensor.off(sensor.SensorId.BAROMETER);
} catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.BAROMETER')<sup>19+</sup>

off(type: SensorId.BAROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;BarometerResponse&gt;): void

Unsubscribes from data of the barometer sensor. Call this method to cancel the subscription when the barometric pressure sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                   | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).BAROMETER                        | Yes  | Sensor type. The value is fixed at **SensorId.BAROMETER**.                  |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[BarometerResponse](#barometerresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.BarometerResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.BAROMETER;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.GRAVITY')<sup>9+</sup> 

off(type: SensorId.GRAVITY, callback?: Callback&lt;GravityResponse&gt;): void

Unsubscribes from data of the gravity sensor. When the gravity sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                               | Mandatory| Description                                                        |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).GRAVITY                      | Yes  | Sensor type. The value is fixed at **SensorId.GRAVITY**.                    |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.GRAVITY, callback1);
  sensor.on(sensor.SensorId.GRAVITY, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.GRAVITY, callback1);
  // Unsubscribe from all callbacks of the SensorId.GRAVITY type.
  sensor.off(sensor.SensorId.GRAVITY);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}

```

## sensor.off('SensorId.GRAVITY')<sup>19+</sup>

off(type: SensorId.GRAVITY, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;GravityResponse&gt;): void

Unsubscribes from data of the gravity sensor. When the gravity sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                               | Mandatory| Description                                                        |
|------------------| --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).GRAVITY                      | Yes  | Sensor type. The value is fixed at **SensorId.GRAVITY**.                    |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[GravityResponse](#gravityresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.GravityResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.GRAVITY;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.GYROSCOPE')<sup>9+</sup> 

off(type: SensorId.GYROSCOPE, callback?: Callback&lt;GyroscopeResponse&gt;): void

Unsubscribes from data of the gyroscope sensor. Call this method to cancel the subscription when gyroscope sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.GYROSCOPE

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).GYROSCOPE                        | Yes  | Sensor type. The value is fixed at **SensorId.GYROSCOPE**.                  |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.GYROSCOPE, callback1);
  sensor.on(sensor.SensorId.GYROSCOPE, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.GYROSCOPE, callback1);
  // Unsubscribe from all callbacks of the SensorId.GYROSCOPE type.
  sensor.off(sensor.SensorId.GYROSCOPE);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.GYROSCOPE')<sup>19+</sup>

off(type: SensorId.GYROSCOPE, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;GyroscopeResponse&gt;): void

Unsubscribes from data of the gyroscope sensor. This API is called to cancel the subscription when gyroscope sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.GYROSCOPE

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                   | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).GYROSCOPE                        | Yes  | Sensor type. The value is fixed at **SensorId.GYROSCOPE**.                  |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.GyroscopeResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.GYROSCOPE;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.GYROSCOPE_UNCALIBRATED')<sup>9+</sup> 

off(type: SensorId.GYROSCOPE_UNCALIBRATED, callback?: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

Unsubscribes from data of the uncalibrated gyroscope sensor. When the uncalibrated gyroscope sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).GYROSCOPE_UNCALIBRATED                | Yes  | Sensor type. The value is fixed at **SensorId.GYROSCOPE_UNCALIBRATED**.     |
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.GYROSCOPE_UNCALIBRATED, callback1);
  sensor.on(sensor.SensorId.GYROSCOPE_UNCALIBRATED, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.GYROSCOPE_UNCALIBRATED, callback1);
  // Unsubscribe from all callbacks of the SensorId.GYROSCOPE_UNCALIBRATED type.
  sensor.off(sensor.SensorId.GYROSCOPE_UNCALIBRATED);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.GYROSCOPE_UNCALIBRATED')<sup>19+</sup>

off(type: SensorId.GYROSCOPE_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

Unsubscribes from data of the uncalibrated gyroscope sensor.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                        | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).GYROSCOPE_UNCALIBRATED                | Yes  | Sensor type. The value is fixed at **SensorId.GYROSCOPE_UNCALIBRATED**.     |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.GyroscopeUncalibratedResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.GYROSCOPE_UNCALIBRATED;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.HALL')<sup>9+</sup> 

off(type: SensorId.HALL, callback?: Callback&lt;HallResponse&gt;): void

Unsubscribes from data of the Hall effect sensor. Call this API when you no longer need to receive data of the Hall effect sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                         | Mandatory| Description                                                        |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).HALL                   | Yes  | Sensor type. The value is fixed at **SensorId.HALL**.                       |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.HALL, callback1);
  sensor.on(sensor.SensorId.HALL, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.HALL, callback1);
  // Unsubscribe from all callbacks of the SensorId.HALL type.
  sensor.off(sensor.SensorId.HALL);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.HALL')<sup>19+</sup>

off(type: SensorId.HALL, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;HallResponse&gt;): void

Unsubscribes from data of the Hall effect sensor. Call this method to unsubscribe from the Hall effect sensor data when it is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                         | Mandatory| Description                                                        |
|------------------| --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).HALL                   | Yes  | Sensor type. The value is fixed at **SensorId.HALL**.                       |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[HallResponse](#hallresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.HallResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.HALL;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.HEART_RATE')<sup>9+</sup> 

off(type: SensorId.HEART_RATE, callback?: Callback&lt;HeartRateResponse&gt;): void

Unsubscribes from data of the heart rate sensor. Call this method to cancel the subscription when the heart rate sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.READ_HEALTH_DATA

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).HEART_RATE                       | Yes  | Sensor type. The value is fixed at **SensorId.HEART_RATE**.                 |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.HEART_RATE, callback1);
  sensor.on(sensor.SensorId.HEART_RATE, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.HEART_RATE, callback1);
  // Unsubscribe from all callbacks of the SensorId.HEART_RATE type.
  sensor.off(sensor.SensorId.HEART_RATE);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.HEART_RATE')<sup>19+</sup>

off(type: SensorId.HEART_RATE, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;HeartRateResponse&gt;): void

Unsubscribes from data of the heart rate sensor. Call this method to cancel the subscription when you no longer need to receive data of the heart rate sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.READ_HEALTH_DATA

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                   | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).HEART_RATE                       | Yes  | Sensor type. The value is fixed at **SensorId.HEART_RATE**.                 |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.HeartRateResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.HEART_RATE;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.HUMIDITY')<sup>9+</sup> 

off(type: SensorId.HUMIDITY, callback?: Callback&lt;HumidityResponse&gt;): void

Unsubscribes from data of the humidity sensor. When the humidity sensor data is no longer needed, call this API to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).HUMIDITY                       | Yes  | Sensor type. The value is fixed at **SensorId.HUMIDITY**.                   |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.HUMIDITY, callback1);
  sensor.on(sensor.SensorId.HUMIDITY, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.HUMIDITY, callback1);
  // Unsubscribe from all callbacks of the SensorId.HUMIDITY type.
  sensor.off(sensor.SensorId.HUMIDITY);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.HUMIDITY')<sup>19+</sup>

off(type: SensorId.HUMIDITY, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;HumidityResponse&gt;): void

Unsubscribes from data of the humidity sensor. When the humidity sensor data is no longer needed, call this API to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                 | Mandatory| Description                                                        |
|------------------| ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).HUMIDITY                       | Yes  | Sensor type. The value is fixed at **SensorId.HUMIDITY**.                   |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[HumidityResponse](#humidityresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.HumidityResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.HUMIDITY;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.LINEAR_ACCELEROMETER')<sup>9+</sup> 

off(type: SensorId.LINEAR_ACCELEROMETER, callback?: Callback&lt;LinearAccelerometerResponse&gt;): void

Unsubscribes from data of the linear acceleration sensor. Call this method to cancel the subscription when the linear acceleration sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).LINEAR_ACCELEROMETER                  | Yes  | Sensor type. The value is fixed at **SensorId.LINEAR_ACCELEROMETER**.        |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.LINEAR_ACCELEROMETER, callback1);
  sensor.on(sensor.SensorId.LINEAR_ACCELEROMETER, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.LINEAR_ACCELEROMETER, callback1);
  // Unsubscribe from all callbacks of the SensorId.LINEAR_ACCELEROMETER type.
  sensor.off(sensor.SensorId.LINEAR_ACCELEROMETER);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.LINEAR_ACCELEROMETER')<sup>19+</sup>

off(type: SensorId.LINEAR_ACCELEROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;LinearAccelerometerResponse&gt;): void

Unsubscribes from data of the linear acceleration sensor. Call this method to cancel the subscription when the linear acceleration sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                        | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).LINEAR_ACCELEROMETER                  | Yes  | Sensor type. The value is fixed at **SensorId.LINEAR_ACCELEROMETER**.        |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.LinearAccelerometerResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.LINEAR_ACCELEROMETER;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.MAGNETIC_FIELD')<sup>9+</sup> 

off(type: SensorId.MAGNETIC_FIELD, callback?: Callback&lt;MagneticFieldResponse&gt;): void

Unsubscribes from data of the magnetic field sensor. When the magnetic field sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD                        | Yes  | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD**.             |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.MAGNETIC_FIELD, callback1);
  sensor.on(sensor.SensorId.MAGNETIC_FIELD, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.MAGNETIC_FIELD, callback1);
  // Unsubscribe from all callbacks of the SensorId.MAGNETIC_FIELD type.
  sensor.off(sensor.SensorId.MAGNETIC_FIELD);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.MAGNETIC_FIELD')<sup>19+</sup>

off(type: SensorId.MAGNETIC_FIELD, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;MagneticFieldResponse&gt;): void

Unsubscribes from data of the magnetic field sensor. When the magnetic field sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                        | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).MAGNETIC_FIELD                        | Yes  | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD**.             |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.MagneticFieldResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.MAGNETIC_FIELD;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.MAGNETIC_FIELD_UNCALIBRATED')<sup>9+</sup> 

off(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback?: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

Unsubscribes from data of the uncalibrated magnetic field sensor. When the uncalibrated magnetic field sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).MAGNETIC_FIELD_UNCALIBRATED           | Yes  | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD_UNCALIBRATED**.|
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback1);
  sensor.on(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback1);
  // Unsubscribe from all callbacks of the SensorId.MAGNETIC_FIELD_UNCALIBRATED type.
  sensor.off(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.MAGNETIC_FIELD_UNCALIBRATED')<sup>19+</sup>

off(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

Unsubscribes from data of the uncalibrated magnetic field sensor. When the uncalibrated magnetic field sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                        | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).MAGNETIC_FIELD_UNCALIBRATED           | Yes  | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD_UNCALIBRATED**.|
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.MagneticFieldUncalibratedResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.ORIENTATION')<sup>9+</sup>

off(type: SensorId.ORIENTATION, callback?: Callback&lt;OrientationResponse&gt;): void

Unsubscribes from data of the orientation sensor. Call this method to unsubscribe from data of the orientation sensor when the data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ORIENTATION                          | Yes  | Sensor type. The value is fixed at **SensorId.ORIENTATION**.                |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.ORIENTATION, callback1);
  sensor.on(sensor.SensorId.ORIENTATION, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.ORIENTATION, callback1);
  // Unsubscribe from all callbacks of the SensorId.ORIENTATION type.
  sensor.off(sensor.SensorId.ORIENTATION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.ORIENTATION')<sup>19+</sup>

off(type: SensorId.ORIENTATION, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;OrientationResponse&gt;): void

Unsubscribes from data of the orientation sensor. Call this method to unsubscribe from data of the orientation sensor when the data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ORIENTATION                          | Yes  | Sensor type. The value is fixed at **SensorId.ORIENTATION**.                |
| sensorInfoParam | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.OrientationResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.ORIENTATION;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.PEDOMETER')<sup>9+</sup>

off(type: SensorId.PEDOMETER, callback?: Callback&lt;PedometerResponse&gt;): void

Unsubscribes from data of the pedometer sensor. Call this method to cancel the subscription when the pedometer sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PEDOMETER                        | Yes  | Sensor type. The value is fixed at **SensorId.PEDOMETER**.                  |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.PEDOMETER, callback1);
  sensor.on(sensor.SensorId.PEDOMETER, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.PEDOMETER, callback1);
  // Unsubscribe from all callbacks of the SensorId.PEDOMETER type.
  sensor.off(sensor.SensorId.PEDOMETER);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.PEDOMETER')<sup>19+</sup>

off(type: SensorId.PEDOMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;PedometerResponse&gt;): void

Unsubscribes from data of the pedometer sensor. When the pedometer sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                   | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).PEDOMETER                        | Yes  | Sensor type. The value is fixed at **SensorId.PEDOMETER**.                  |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[PedometerResponse](#pedometerresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.PedometerResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.PEDOMETER;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.PEDOMETER_DETECTION')<sup>9+</sup> 

off(type: SensorId.PEDOMETER_DETECTION, callback?: Callback&lt;PedometerDetectionResponse&gt;): void

Unsubscribes from data of the pedometer detection sensor. Call this method when you no longer need to receive data of the pedometer detection sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PEDOMETER_DETECTION                   | Yes  | Sensor type. The value is fixed at **SensorId.PEDOMETER_DETECTION**.        |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.PEDOMETER_DETECTION, callback1);
  sensor.on(sensor.SensorId.PEDOMETER_DETECTION, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.PEDOMETER_DETECTION, callback1);
  // Unsubscribe from all callbacks of the SensorId.PEDOMETER_DETECTION type.
  sensor.off(sensor.SensorId.PEDOMETER_DETECTION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.PEDOMETER_DETECTION')<sup>19+</sup>

off(type: SensorId.PEDOMETER_DETECTION, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;PedometerDetectionResponse&gt;): void

Unsubscribes from data of the pedometer detection sensor. Call this method when you no longer need to receive data of the pedometer detection sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                        | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).PEDOMETER_DETECTION                   | Yes  | Sensor type. The value is fixed at **SensorId.PEDOMETER_DETECTION**.        |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.PedometerDetectionResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.PEDOMETER_DETECTION;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.PROXIMITY')<sup>9+</sup>  

off(type: SensorId.PROXIMITY, callback?: Callback&lt;ProximityResponse&gt;): void

Unsubscribes from data of the proximity sensor. When the proximity sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).PROXIMITY                        | Yes  | Sensor type. The value is fixed at **SensorId.PROXIMITY**.                  |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.PROXIMITY, callback1);
  sensor.on(sensor.SensorId.PROXIMITY, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.PROXIMITY, callback1);
  // Unsubscribe from all callbacks of the SensorId.PROXIMITY type.
  sensor.off(sensor.SensorId.PROXIMITY);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.PROXIMITY')<sup>19+</sup>

off(type: SensorId.PROXIMITY, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;ProximityResponse&gt;): void

Unsubscribes from data of the proximity sensor. When the proximity sensor data is no longer needed, call this method to cancel the subscription. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name            | Type                                                   | Mandatory| Description                                                        |
|-----------------| ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type            | [SensorId](#sensorid9).PROXIMITY                        | Yes  | Sensor type. The value is fixed at **SensorId.PROXIMITY**.                  |
| sensorInfoParam | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback        | Callback&lt;[ProximityResponse](#proximityresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.ProximityResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.PROXIMITY;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.ROTATION_VECTOR')<sup>9+</sup>

off(type: SensorId.ROTATION_VECTOR, callback?: Callback&lt;RotationVectorResponse&gt;): void

Unsubscribes from data of the rotation vector sensor. Call this method to cancel the subscription when the rotation vector sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).ROTATION_VECTOR                       | Yes  | Sensor type. The value is fixed at **SensorId.ROTATION_VECTOR**.            |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.ROTATION_VECTOR, callback1);
  sensor.on(sensor.SensorId.ROTATION_VECTOR, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.ROTATION_VECTOR, callback1);
  // Unsubscribe from all callbacks of the SensorId.ROTATION_VECTOR type.
  sensor.off(sensor.SensorId.ROTATION_VECTOR);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.ROTATION_VECTOR')<sup>19+</sup>

off(type: SensorId.ROTATION_VECTOR, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;RotationVectorResponse&gt;): void

Unsubscribes from data of the rotation vector sensor. Call this method to cancel the subscription when the rotation vector sensor data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                        | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).ROTATION_VECTOR                       | Yes  | Sensor type. The value is fixed at **SensorId.ROTATION_VECTOR**.            |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.RotationVectorResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.ROTATION_VECTOR;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.SIGNIFICANT_MOTION')<sup>9+</sup>

off(type: SensorId.SIGNIFICANT_MOTION, callback?: Callback&lt;SignificantMotionResponse&gt;): void

Unsubscribes from significant motion sensor data. Call this API to unsubscribe from significant motion sensor data when it is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).SIGNIFICANT_MOTION                    | Yes  | Sensor type. The value is fixed at **SensorId.SIGNIFICANT_MOTION**.         |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.SIGNIFICANT_MOTION, callback1);
  sensor.on(sensor.SensorId.SIGNIFICANT_MOTION, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.SIGNIFICANT_MOTION, callback1);
  // Unsubscribe from all callbacks of the SensorId.SIGNIFICANT_MOTION type.
  sensor.off(sensor.SensorId.SIGNIFICANT_MOTION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.SIGNIFICANT_MOTION')<sup>19+</sup>

off(type: SensorId.SIGNIFICANT_MOTION, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;SignificantMotionResponse&gt;): void

Unsubscribes from significant motion sensor data. Call this API to unsubscribe from significant motion sensor data when it is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                        | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).SIGNIFICANT_MOTION                    | Yes  | Sensor type. The value is fixed at **SensorId.SIGNIFICANT_MOTION**.         |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.SignificantMotionResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.SIGNIFICANT_MOTION;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('SensorId.WEAR_DETECTION')<sup>9+</sup>

off(type: SensorId.WEAR_DETECTION, callback?: Callback&lt;WearDetectionResponse&gt;): void

Unsubscribes from data of the wear detection sensor. Call this method to unsubscribe from data of the wear detection sensor when the data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).WEAR_DETECTION                    | Yes  | Sensor type. The value is fixed at [SensorId](#sensorid9).WEAR_DETECTION.             |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  sensor.on(sensor.SensorId.WEAR_DETECTION, callback1);
  sensor.on(sensor.SensorId.WEAR_DETECTION, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.WEAR_DETECTION, callback1);
  // Unsubscribe from all callbacks of the SensorId.WEAR_DETECTION type.
  sensor.off(sensor.SensorId.WEAR_DETECTION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.off('SensorId.WEAR_DETECTION')<sup>19+</sup>

off(type: SensorId.WEAR_DETECTION, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;WearDetectionResponse&gt;): void

Unsubscribes from data of the wear detection sensor. Call this method to unsubscribe from data of the wear detection sensor when the data is no longer needed. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                                        | Mandatory| Description                                                        |
|------------------| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type             | [SensorId](#sensorid9).WEAR_DETECTION                        | Yes  | Sensor type. The value is fixed at **SensorId.WEAR_DETECTION**.             |
| sensorInfoParam  | [SensorInfoParam](#sensorinfoparam19) |  No| Sensor settings parameter. You can cancel the subscription to a specified sensor on a specified device by specifying **deviceId** and **sensorIndex**. If this parameter is not passed, the subscription to all sensors of this type on the local device is canceled by default.|
| callback         | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.WearDetectionResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.WEAR_DETECTION;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // Use try catch to capture possible exceptions.
  try {
    // Query all sensors.
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // Obtain the target sensor based on the actual service logic.
    const targetSensor = sensorList
      // Filter all sensors with deviceId 1 and sensorId 2 as required. This example is for reference only. You need to adjust the filtering logic accordingly.
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // Select the sensor with sensorIndex 0 among all sensors of the same type.
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // Subscribe to sensor events.
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
  // Use try catch to capture possible exceptions.
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

## sensor.off('sensorStatusChange')<sup>19+<sup>

off(type: 'sensorStatusChange', callback?: Callback&lt;SensorStatusEvent&gt;): void

Disables listening for sensor status changes. Call this API when you no longer need to detect sensor status changes. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | string         | Yes  | Event type. The value **sensorStatusChange** indicates the sensor status change event.            |
| callback | Callback&lt;[SensorStatusEvent](#sensorstatusevent19)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  const statusChangeCallback = (data: sensor.SensorStatusEvent) => {
    console.info('sensorStatusChange : ' + JSON.stringify(data));
  }
  const statusChangeCallback2 = (data: sensor.SensorStatusEvent) => {
    console.info('sensorStatusChange2 : ' + JSON.stringify(data));
  }
  // Register two callback listeners for device online events.
  sensor.on('sensorStatusChange', statusChangeCallback);
  sensor.on('sensorStatusChange', statusChangeCallback2);
  
  // Unregister the first listener after 3 seconds.
  setTimeout(() => {
    sensor.off('sensorStatusChange', statusChangeCallback);
  }, 3000);
  // Unregister the other listener after 5 seconds.
  setTimeout(() => {
    sensor.off('sensorStatusChange');
  }, 5000);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


## sensor.getSensorListByDeviceSync<sup>19+</sup> 

getSensorListByDeviceSync(deviceId?: number): Array&lt;Sensor&gt; 

Obtains the information about all sensors on the device. **getSensorListByDeviceSync** returns information about all sensors on the device, and **getSingleSensorByDeviceSync** returns information about a specified sensor.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name         | Type                                                        | Mandatory| Description    |
| --------------- | ------------------------------------------------------------ | ---- |--------|
| deviceId | number                 | No  | Device ID. The default value is **-1**, indicating the local device. You can use [getSensorList](#sensorgetsensorlist9) or [sensorStatusChange](#sensoronsensorstatuschange19) to obtain the device ID.|


**Return value**

| Type                                                      | Description          |
| ---------------------------------------------------------- | -------------- |
| Array&lt;[Sensor](#sensor9)&gt;           | Sensor attribute list.                 |


**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const deviceId = 1;
  // The first deviceId is optional. By default, it is set to the ID of the local device.
  const sensorList: sensor.Sensor[] = sensor.getSensorListByDeviceSync(deviceId);
  console.info(`sensorList length: ${sensorList.length}`);
  console.info(`sensorList: ${JSON.stringify(sensorList)}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get sensorList. Code: ${e.code}, message: ${e.message}`);
}
```


## sensor.getSingleSensorByDeviceSync<sup>19+</sup> 

getSingleSensorByDeviceSync(type: SensorId, deviceId?: number): Array&lt;Sensor&gt;

Obtains information about the sensor of a specific type. If peripherals exist and no device ID is specified, the obtained sensors will be all local and peripheral sensors that match the specified sensor type. If no peripherals exist, only local sensors are obtained.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name         | Type                                                        | Mandatory| Description      |
| --------------- | ------------------------------------------------------------ | ---- |----------|
| type     | [SensorId](#sensorid9) | Yes  | Sensor type.|
| deviceId | number                 | No  | Device ID. The default value is **-1**, indicating the local device. You can use [getSensorList](#sensorgetsensorlist9) or [sensorStatusChange](#sensoronsensorstatuschange19) to obtain the device ID.|


**Return value**

| Type                                                      | Description          |
| ---------------------------------------------------------- | -------------- |
| Array&lt;[Sensor](#sensor9)&gt;           | Sensor attribute list.                 |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const deviceId = 1;
  // The second deviceId is optional.
  const sensorList: sensor.Sensor[] = sensor.getSingleSensorByDeviceSync(sensor.SensorId.ACCELEROMETER, deviceId);
  console.info(`sensorList length: ${sensorList.length}`);
  console.info(`sensorList Json: ${JSON.stringify(sensorList)}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get sensorList. Code: ${e.code}, message: ${e.message}`);
}
```


## sensor.getGeomagneticInfo<sup>9+</sup> 

getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: number, callback: AsyncCallback&lt;GeomagneticResponse&gt;): void

Obtains the geomagnetic field of a geographic location at a certain time. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name         | Type                                                        | Mandatory| Description                              |
| --------------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| locationOptions | [LocationOptions](#locationoptions)                          | Yes  | Geographic location, including the longitude, latitude, and altitude.                        |
| timeMillis      | number                                                       | Yes  | Time when the magnetic declination is obtained. The value is a Unix timestamp, in ms. This parameter indicates the number of milliseconds since 1970-01-01 00:00:00-00 UTC.  The value must be a positive integer. |
| callback        | AsyncCallback&lt;[GeomagneticResponse](#geomagneticresponse)&gt; | Yes  | Callback used to return the geomagnetic field.                |

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.getGeomagneticInfo({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000,
      (err: BusinessError, data: sensor.GeomagneticResponse) => {
    if (err) {
      console.error(`Failed to get geomagneticInfo. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in getting geomagneticInfo x" + data.x);
    console.info("Succeeded in getting geomagneticInfo y" + data.y);
    console.info("Succeeded in getting geomagneticInfo z" + data.z);
    console.info("Succeeded in getting geomagneticInfo geomagneticDip" + data.geomagneticDip);
    console.info("Succeeded in getting geomagneticInfo deflectionAngle" + data.deflectionAngle);
    console.info("Succeeded in getting geomagneticInfo levelIntensity" + data.levelIntensity);
    console.info("Succeeded in getting geomagneticInfo totalIntensity" + data.totalIntensity);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get geomagneticInfo. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getGeomagneticInfo<sup>9+</sup> 

getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: number): Promise&lt;GeomagneticResponse&gt;

Obtains the geomagnetic field of a geographic location at a certain time. This API uses a promise to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name         | Type                               | Mandatory| Description                              |
| --------------- | ----------------------------------- | ---- | ---------------------------------- |
| locationOptions | [LocationOptions](#locationoptions) | Yes  | Geographic location, including the longitude, latitude, and altitude.                        |
| timeMillis      | number                              | Yes  | Time when the magnetic declination is obtained. The value is a Unix timestamp, in ms. This parameter indicates the number of milliseconds since 1970-01-01 00:00:00-00 UTC.  The value must be a positive integer. |

**Return value**

| Type                                                      | Description          |
| ---------------------------------------------------------- | -------------- |
| Promise&lt;[GeomagneticResponse](#geomagneticresponse)&gt; | Promise used to return the geomagnetic field.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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
  }, (err: BusinessError) => {
    console.error(`Failed to get geomagneticInfo. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get geomagneticInfo. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getDeviceAltitude<sup>9+</sup> 

getDeviceAltitude(seaPressure: number, currentPressure: number, callback: AsyncCallback&lt;number&gt;): void

Obtains the altitude based on the atmospheric pressure. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name         | Type                       | Mandatory| Description                                 |
| --------------- | --------------------------- | ---- | ------------------------------------- |
| seaPressure     | number                      | Yes  | Sea-level atmospheric pressure, in hPa.        |
| currentPressure | number                      | Yes  | Specified atmospheric pressure, in hPa.|
| callback        | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the altitude, in meters. |

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  let seaPressure = 1013.2;
  let currentPressure = 1500.0;
  sensor.getDeviceAltitude(seaPressure, currentPressure, (err: BusinessError, data: number) => {
    if (err) {
      console.error(`Failed to get altitude. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting altitude: ' + data);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get altitude. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getDeviceAltitude<sup>9+</sup> 

getDeviceAltitude(seaPressure: number, currentPressure: number): Promise&lt;number&gt;

Obtains the altitude based on the atmospheric pressure. This API uses a promise to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name         | Type  | Mandatory| Description                                 |
| --------------- | ------ | ---- | ------------------------------------- |
| seaPressure     | number | Yes  | Sea-level atmospheric pressure, in hPa.        |
| currentPressure | number | Yes  | Specified atmospheric pressure, in hPa.|

**Return value**

| Type                 | Description                                |
| --------------------- | ------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the altitude, in meters.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.getInclination<sup>9+</sup> 

getInclination(inclinationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;number&gt;): void

Obtains the magnetic dip based on the inclination matrix. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name           | Type                       | Mandatory| Description                        |
| ----------------- | --------------------------- | ---- | ---------------------------- |
| inclinationMatrix | Array&lt;number&gt;         | Yes  | Inclination matrix.              |
| callback          | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the magnetic dip, in radians.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // inclinationMatrix can be 3*3 or 4*4.
  let inclinationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ]
  sensor.getInclination(inclinationMatrix, (err: BusinessError, data: number) => {
    if (err) {
      console.error(`Failed to get inclination. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting inclination: ' + data);
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get inclination. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getInclination<sup>9+</sup> 

 getInclination(inclinationMatrix: Array&lt;number&gt;): Promise&lt;number&gt;

Obtains the magnetic dip based on the inclination matrix. This API uses a promise to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name           | Type               | Mandatory| Description          |
| ----------------- | ------------------- | ---- | -------------- |
| inclinationMatrix | Array&lt;number&gt; | Yes  | Inclination matrix.|

**Return value**

| Type                 | Description                        |
| --------------------- | ---------------------------- |
| Promise&lt;number&gt; | Promise used to return the magnetic dip, in radians.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // inclinationMatrix can be 3*3 or 4*4.
  let inclinationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ]
  const promise = sensor.getInclination(inclinationMatrix);
  promise.then((data: number) => {
    console.info('Succeeded in getting inclination: ' + data);
  }, (err: BusinessError) => {
    console.error(`Failed to get inclination. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get inclination. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getAngleVariation<sup>9+</sup>

getAngleVariation(currentRotationMatrix: Array&lt;number&gt;, preRotationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

Obtains the angle change between two rotation matrices. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name               | Type                                    | Mandatory| Description                             |
| --------------------- | ---------------------------------------- | ---- | --------------------------------- |
| currentRotationMatrix | Array&lt;number&gt;                      | Yes  | Current rotation matrix.               |
| preRotationMatrix     | Array&lt;number&gt;                      | Yes  | The other rotation matrix.                   |
| callback              | AsyncCallback&lt;Array&lt;number&gt;&gt; | Yes  | Asynchronous callback used to return the rotation angles around the z, x, and y axes, in degrees (°).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // The rotation matrix can be 3*3 or 4*4.
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
  sensor.getAngleVariation(currentRotationMatrix, preRotationMatrix, (err: BusinessError, data: Array<number>) => {
    if (err) {
      console.error(`Failed to get angle variation. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    if (data.length < 3) {
      console.error("Failed to get angle variation, length" + data.length);
      return;
    }
    console.info("Z: " + data[0]);
    console.info("X: " + data[1]);
    console.info("Y: " + data[2]);
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get angle variation. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getAngleVariation<sup>9+</sup>

getAngleVariation(currentRotationMatrix: Array&lt;number&gt;, preRotationMatrix: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt; 

Obtains the angle change between two rotation matrices. This API uses a promise to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name               | Type               | Mandatory| Description              |
| --------------------- | ------------------- | ---- | ------------------ |
| currentRotationMatrix | Array&lt;number&gt; | Yes  | Current rotation matrix.|
| preRotationMatrix     | Array&lt;number&gt; | Yes  | The other rotation matrix.                 |

**Return value**

| Type                              | Description                             |
| ---------------------------------- | --------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation angles around the z, x, and y axes, in degrees (°).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // The rotation matrix can be 3*3 or 4*4.
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
      return;
    }
    console.info("Z: " + data[0]);
    console.info("X: " + data[1]);
    console.info("Y: " + data[2]);
  }, (err: BusinessError) => {
    console.error(`Failed to get angle variation. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get angle variation. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getRotationMatrix<sup>9+</sup> 

getRotationMatrix(rotationVector: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

Obtains the rotation matrix from a rotation vector. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name        | Type                                    | Mandatory| Description          |
| -------------- | ---------------------------------------- | ---- | -------------- |
| rotationVector | Array&lt;number&gt;                      | Yes  | Rotation vector.|
| callback       | AsyncCallback&lt;Array&lt;number&gt;&gt; | Yes  | Callback used to return the rotation matrix.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.getRotationMatrix<sup>9+</sup>

getRotationMatrix(rotationVector: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt; 

Obtains the rotation matrix from a rotation vector. This API uses a promise to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name        | Type               | Mandatory| Description          |
| -------------- | ------------------- | ---- | -------------- |
| rotationVector | Array&lt;number&gt; | Yes  | Rotation vector.|

**Return value**

| Type                              | Description          |
| ---------------------------------- | -------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation matrix.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.transformRotationMatrix<sup>9+</sup> 

transformRotationMatrix(inRotationVector: Array&lt;number&gt;, coordinates: CoordinatesOptions, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

Transforms a rotation vector based on the coordinate system. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name          | Type                                     | Mandatory| Description                  |
| ---------------- | ----------------------------------------- | ---- | ---------------------- |
| inRotationVector | Array&lt;number&gt;                       | Yes  | Rotation vector.        |
| coordinates      | [CoordinatesOptions](#coordinatesoptions) | Yes  | Rotation vector to transform.      |
| callback         | AsyncCallback&lt;Array&lt;number&gt;&gt;  | Yes  | Callback used to return the rotation vector after being transformed.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  let rotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  sensor.transformRotationMatrix(rotationMatrix, { x: 1, y: 3 }, (err: BusinessError, data: Array<number>) => {
    if (err) {
      console.error(`Failed to transform rotationMatrix. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + '] = ' + data[i]);
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to transform rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.transformRotationMatrix<sup>9+</sup>

transformRotationMatrix(inRotationVector: Array&lt;number&gt;, coordinates: CoordinatesOptions): Promise&lt;Array&lt;number&gt;&gt;

Transforms a rotation vector based on the coordinate system. This API uses a promise to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name          | Type                                     | Mandatory| Description            |
| ---------------- | ----------------------------------------- | ---- | ---------------- |
| inRotationVector | Array&lt;number&gt;                       | Yes  | Rotation vector.  |
| coordinates      | [CoordinatesOptions](#coordinatesoptions) | Yes  | Rotation vector to transform.|

**Return value**

| Type                              | Description                  |
| ---------------------------------- | ---------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation vector after being transformed.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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
  }, (err: BusinessError) => {
    console.error(`Failed to transform rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to transform rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getQuaternion<sup>9+</sup> 

getQuaternion(rotationVector: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void 

Obtains the quaternion from a rotation vector. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name        | Type                                    | Mandatory| Description          |
| -------------- | ---------------------------------------- | ---- | -------------- |
| rotationVector | Array&lt;number&gt;                      | Yes  | Rotation vector.|
| callback       | AsyncCallback&lt;Array&lt;number&gt;&gt; | Yes  | Callback used to return the quaternion.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  sensor.getQuaternion(rotationVector, (err: BusinessError, data: Array<number>) => {
    if (err) {
      console.error(`Failed to get quaternion. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get quaternion. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getQuaternion<sup>9+</sup>

getQuaternion(rotationVector: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

Obtains the quaternion from a rotation vector. This API uses a promise to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name        | Type               | Mandatory| Description          |
| -------------- | ------------------- | ---- | -------------- |
| rotationVector | Array&lt;number&gt; | Yes  | Rotation vector.|

**Return value**

| Type                              | Description        |
| ---------------------------------- | ------------ |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the quaternion..|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
    let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
    const promise = sensor.getQuaternion(rotationVector);
    promise.then((data: Array<number>) => {
        for (let i = 0; i < data.length; i++) {
            console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
        }
    }, (err: BusinessError) => {
        console.error(`Failed to get quaternion. Code: ${err.code}, message: ${err.message}`);
    });
} catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to get quaternion. Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getOrientation<sup>9+</sup>

getOrientation(rotationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void 

Obtains the device direction based on the rotation matrix. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name        | Type                                    | Mandatory| Description                             |
| -------------- | ---------------------------------------- | ---- | --------------------------------- |
| rotationMatrix | Array&lt;number&gt;                      | Yes  | Rotation matrix.                   |
| callback       | AsyncCallback&lt;Array&lt;number&gt;&gt; | Yes  | Asynchronous callback used to return the rotation angles around the z, x, and y axes, in degrees (°).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.getOrientation<sup>9+</sup>

getOrientation(rotationMatrix: Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

Obtains the device direction based on the rotation matrix. This API uses a promise to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name        | Type               | Mandatory| Description          |
| -------------- | ------------------- | ---- | -------------- |
| rotationMatrix | Array&lt;number&gt; | Yes  | Rotation matrix.|

**Return value**

| Type                              | Description                             |
| ---------------------------------- | --------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation angles around the z, x, and y axes, in degrees (°).|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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
    console.error(`Failed to getOrientation. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to getOrientation Code: ${e.code}, message: ${e.message}`);
}
```

## sensor.getRotationMatrix<sup>9+</sup> 

getRotationMatrix(gravity: Array&lt;number&gt;, geomagnetic: Array&lt;number&gt;, callback: AsyncCallback&lt;RotationMatrixResponse&gt;): void 

Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name     | Type                                                        | Mandatory| Description          |
| ----------- | ------------------------------------------------------------ | ---- | -------------- |
| gravity     | Array&lt;number&gt;                                          | Yes  | Gravity vector.|
| geomagnetic | Array&lt;number&gt;                                          | Yes  | Geomagnetic vector.|
| callback    | AsyncCallback&lt;[RotationMatrixResponse](#rotationmatrixresponse)&gt; | Yes  | Callback used to return the rotation matrix.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.getRotationMatrix<sup>9+</sup> 

getRotationMatrix(gravity: Array&lt;number&gt;, geomagnetic: Array&lt;number&gt;): Promise&lt;RotationMatrixResponse&gt;

Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses a promise to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name     | Type               | Mandatory| Description          |
| ----------- | ------------------- | ---- | -------------- |
| gravity     | Array&lt;number&gt; | Yes  | Gravity vector.|
| geomagnetic | Array&lt;number&gt; | Yes  | Geomagnetic vector.|

**Return value**

| Type                                                        | Description          |
| ------------------------------------------------------------ | -------------- |
| Promise&lt;[RotationMatrixResponse](#rotationmatrixresponse)&gt; | Promise used to return the rotation matrix. The **RotationMatrixResponse** object contains the rotation matrix and tilt matrix of the device, which can be used to calculate the posture and orientation of the device.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

## sensor.getSensorList<sup>9+</sup>

getSensorList(callback: AsyncCallback&lt;Array&lt;Sensor&gt;&gt;): void

Obtains information about all sensors on the device. This API uses an asynchronous callback to return the result. To obtain the sensor list synchronously, use **getSensorListSync**.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                          | Mandatory| Description            |
| -------- | ---------------------------------------------- | ---- | ---------------- |
| callback | AsyncCallback&lt;Array&lt;[Sensor](#sensor9)&gt;&gt; | Yes  | Callback used to return the sensor list.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

Obtains information about all sensors on the device. This API uses a promise to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Return value**

| Type                                    | Description            |
| ---------------------------------------- | ---------------- |
| Promise&lt;Array&lt;[Sensor](#sensor9)&gt;&gt; | Promise used to return the sensor list. Each **Sensor** object contains the sensor type ID, name, version, manufacturer, maximum range, resolution, power, and other attributes.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

Obtains information about all sensors on the device. This API returns the result synchronously.

**System capability**: SystemCapability.Sensors.Sensor

**Return value**

| Type                                   | Description                            |
| --------------------------------------- | -------------------------------- |
| Array&lt;[Sensor](#sensor9)&gt; | List of sensor attributes.|

**Error codes**

For details about the following error codes, see [Sensor Error Codes](errorcode-sensor.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message          |
| -------- | ------------------ |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

Obtains information about the sensor of a specific type. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                   | Mandatory| Description            |
| -------- | --------------------------------------- | ---- | ---------------- |
| type     | [SensorId](#sensorid9)                  | Yes  | Sensor type.    |
| callback | AsyncCallback&lt;[Sensor](#sensor9)&gt; | Yes  | Callback used to return the sensor information.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |
| 14500102 | The sensor is not supported by the device. [since 12]                  |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  sensor.getSingleSensor(sensor.SensorId.ACCELEROMETER, (err: BusinessError, data: sensor.Sensor) => {
    if (err) {
      console.error(`Failed to get singleSensor. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting sensor: ' + JSON.stringify(data));
    sensor.on(sensor.SensorId.ACCELEROMETER, (data: sensor.AccelerometerResponse) => {
      console.info('Succeeded in invoking on. X-coordinate component: ' + data.x);
      console.info('Succeeded in invoking on. Y-coordinate component: ' + data.y);
      console.info('Succeeded in invoking on. Z-coordinate component: ' + data.z);
    }, { interval: 100000000 });
    setTimeout(() => {
      sensor.off(sensor.SensorId.ACCELEROMETER);
    }, 500);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get singleSensor. Code: ${e.code}, message: ${e.message}`);
}
```

##  sensor.getSingleSensor<sup>9+</sup>

 getSingleSensor(type: SensorId): Promise&lt;Sensor&gt;

Obtains information about the sensor of a specific type. This API uses a promise to return the result.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name| Type                  | Mandatory| Description        |
| ------ | ---------------------- | ---- | ------------ |
| type   | [SensorId](#sensorid9) | Yes  | Sensor type.|

**Return value**

| Type                             | Description                        |
| --------------------------------- | ---------------------------- |
| Promise&lt;[Sensor](#sensor9)&gt; | Promise used to return the sensor information.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |
| 14500102 | The sensor is not supported by the device. [since 12]                   |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
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

Obtains information about the sensor of a specific type. This API returns the result synchronously.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name| Type                  | Mandatory| Description        |
| ------ | ---------------------- | ---- | ------------ |
| type   | [SensorId](#sensorid9) | Yes  | Sensor type.|

**Return value**

| Type  | Description                        |
| ------ | ---------------------------- |
| Sensor | Sensor information.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |
| 14500102 | The sensor is not supported by the device.                   |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  let ret = sensor.getSingleSensorSync(sensor.SensorId.ACCELEROMETER);
  console.info('Succeeded in getting sensor: ' + JSON.stringify(ret));
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get singleSensor . Code: ${e.code}, message: ${e.message}`);
}
```


## SensorId<sup>9+</sup>

Enumerates the sensor types.

**System capability**: SystemCapability.Sensors.Sensor

| Name                       | Value  | Description                                                        |
| --------------------------- | ---- | ------------------------------------------------------------ |
| ACCELEROMETER               | 1    | Accelerometer sensor, which is used to measure the acceleration of the device.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| GYROSCOPE                   | 2    | Gyroscope sensor, which is used to measure the angular velocity of the device.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| AMBIENT_LIGHT               | 5    | Ambient light sensor, which is used to measure the ambient light intensity.                                              |
| MAGNETIC_FIELD              | 6    | Magnetic field sensor, which is used to measure the ambient magnetic field strength around the device.                                                |
| BAROMETER                   | 8    | Barometric pressure sensor, which is used to measure atmospheric pressure.                                              |
| HALL                        | 10   | Hall effect sensor, which is used to detect whether there is a magnetic force around the device.                                                |
| PROXIMITY                   | 12   | Proximity sensor, which is used to detect the proximity between an object and the device display.                                              |
| HUMIDITY                    | 13   | Humidity sensor, which is used to measure the relative humidity of the environment.                                              |
| ORIENTATION                 | 256  | Orientation sensor, which is used to measure the rotation angle of the device.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| GRAVITY                     | 257  | Gravity sensor, which is used to measure the gravity acceleration of the device.                                                |
| LINEAR_ACCELEROMETER        | 258  | Linear acceleration sensor, which is used to measure the linear acceleration of the device excluding the effect of gravity.                                          |
| ROTATION_VECTOR             | 259  | Rotation vector sensor type, which is used to describe the rotation status of the device relative to a reference direction.                                            |
| AMBIENT_TEMPERATURE         | 260  | Ambient temperature sensor, which is used to measure the ambient temperature.                                            |
| MAGNETIC_FIELD_UNCALIBRATED | 261  | Uncalibrated magnetic field sensor, which is used to measure the uncalibrated ambient magnetic field strength and its bias.                                          |
| GYROSCOPE_UNCALIBRATED      | 263  | Uncalibrated gyroscope sensor, which is used to measure the uncalibrated angular velocity of the device and its bias.                                        |
| SIGNIFICANT_MOTION          | 264  | Significant motion sensor, which is used to detect whether the device is moving significantly.                                            |
| PEDOMETER_DETECTION         | 265  | Pedometer detection sensor, which is used to detect the step counting action of a user.                                        |
| PEDOMETER                   | 266  | Step counter sensor, which is used to count the number of steps a user has taken.                                                |
| HEART_RATE                  | 278  | Heart rate sensor, which is used to measure the heart rate of a user.                                                |
| WEAR_DETECTION              | 280  | Wear detection sensor, which is used to detect whether the device is being worn.                                              |
| ACCELEROMETER_UNCALIBRATED  | 281  | Uncalibrated acceleration sensor, which is used to measure the uncalibrated acceleration of the device and its bias.                                      |
| FUSION_PRESSURE<sup>22+</sup>             | 283  | Fused pressure sensor, which is used to measure the fusion pressure value. This sensor is available only on smart watches.                       |


## SensorInfoParam<sup>19+</sup>

Defines sensor parameters, including **deviceId** and **sensorIndex**.

**System capability**: SystemCapability.Sensors.Sensor

**Atomic service API**: This API can be used in atomic services since API version 19.


| Name         | Type    | Read-Only | Optional | Description            |
|--------------|----------|-------|------|----------------- |
| deviceId    | number    | No   | Yes   | ID of the device to which the target sensor belongs. The default value is **-1**, which indicates the local device. You can obtain the ID of a remote device through [sensor.on('sensorStatusChange')](#sensoronsensorstatuschange19) or [getSensorList](#sensorgetsensorlist9).     |
| sensorIndex | number    | No   | Yes   | Index of the target sensor. A sensor type may have multiple instances. The default value is **0**, which indicates the default sensor on the device. You can use [getSensorList](#sensorgetsensorlist9) or [sensor.on('sensorStatusChange')](#sensoronsensorstatuschange19) to obtain the sensor index.|


## SensorStatusEvent<sup>19+</sup>

Defines the sensor status change event, which is used to describe the sensor online and offline events.

**System capability**: SystemCapability.Sensors.Sensor

| Name          | Type    | Read-Only| Optional| Description                         |
|----------------|---------|-----|-----|-----------------------------|
| timestamp      | number  | No | No | Timestamp when an event occurs. Period from the time when the device is powered on until the event occurs, in ms.                  |
| sensorId       | number  | No | No | Sensor type ID, corresponding to the enumerated values of [SensorId](#sensorid9).                     |
| sensorIndex    | number  | No | No | Sensor index. Multiple instances of sensors of the same type may exist, which are distinguished by **sensorIndex**.                     |
| isSensorOnline | boolean | No | No | Whether a sensor is online. The value **true** indicates that the sensor is online, and the value **false** indicates that the sensor is offline.|
| deviceId       | number  | No | No | Device ID. The value **-1** indicates a local device, and other values indicate remote devices.                      |
| deviceName     | string  | No | No | Device name, which identifies the source device of the sensor.                      |

## SensorAccuracy<sup>11+</sup>

Enumerates the accuracy levels of sensor data.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor

| Name   | Value| Description                    |
| --------- | ---- | ------------------------ |
| ACCURACY_UNRELIABLE | 0   | Unreliable sensor data, which has the lowest accuracy level. The data reliability cannot be ensured.|
| ACCURACY_LOW | 1   | Low-accuracy sensor data, which is of low accuracy and is applicable only to rough estimation scenarios.|
| ACCURACY_MEDIUM | 2   | Medium-accuracy sensor data, which is of medium accuracy and is applicable to common application scenarios.|
| ACCURACY_HIGH | 3   | High-accuracy sensor data, which is of high accuracy and is applicable to scenarios that require high precision.|

## Response

Defines the base class for the timestamp and accuracy information of sensor data. All sensor response types inherit from this class.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor

| Name     | Type  | Read-Only| Optional| Description                    |
| --------- | ------ | ---- | ---- | ------------------------ |
| timestamp | number | No  | No  | Timestamp when the sensor reports data. Time from device startup to data reporting, in nanoseconds.|
| accuracy<sup>11+</sup> | [SensorAccuracy](#sensoraccuracy11)<sup>11+</sup> | No  | No  | Accuracy of the sensor data, indicating the reliability of the reported data.|

## Sensor<sup>9+</sup>

Describes the sensor information.

**System capability**: SystemCapability.Sensors.Sensor

| Name                         | Type     | Read-Only| Optional| Description              |
|-----------------------------|---------|----|----|------------------|
| sensorName                  | string  | No | No | Sensor name, which identifies the type and model of the sensor.          |
| vendorName                  | string  | No | No | Sensor vendor name, which identifies the sensor manufacturer.         |
| firmwareVersion             | string  | No | No | Sensor firmware version, which identifies the current version of the sensor firmware.        |
| hardwareVersion             | string  | No | No | Sensor hardware version.        |
| sensorId                    | number  | No | No | Sensor type ID, corresponding to the enumerated values of [SensorId](#sensorid9).        |
| maxRange                    | number  | No | No | Maximum measurement range of the sensor. The unit depends on the sensor type (for example, m/s² for an acceleration sensor).    |
| minSamplePeriod             | number  | No | No | Minimum sampling period of the sensor, in ns      |
| maxSamplePeriod             | number  | No | No | Maximum sampling period of the sensor, in ns      |
| precision                   | number  | No | No | Precision of the sensor. The unit depends on the sensor type.          |
| power                       | number  | No | No | Estimated power consumption of the sensor, in mA.|
| sensorIndex<sup>19+</sup>   | number  | No | Yes | Sensor index. Multiple instances of the same type of sensor may exist, which are distinguished by **sensorIndex**. The default value is **0**.          |
| deviceId<sup>19+</sup>      | number  | No | Yes | Device ID. The value is **-1** indicates the local device. Default value: **-1**.           |
| deviceName<sup>19+</sup>    | string  | No | Yes | Device name, which identifies the source device of the sensor.           |
| isLocalSensor<sup>19+</sup> | boolean | No | Yes | Whether the sensor is a local sensor. The **true** indicates a local sensor, and **false** indicates a non-local sensor (that is, a sensor on a remote device). The default value is **true**.|
| isMockSensor<sup>23+</sup> | boolean | No | Yes | Indicates whether the sensor is a mock sensor. The value **true** indicates a mock sensor, and **false** indicates a real sensor. The default value is **false**.|

## AccelerometerResponse

Describes the acceleration sensor data. It extends from [Response](#response).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor


| Name| Type  | Read-Only| Optional| Description                                                      |
| ---- | ------ | ---- | ---- | ---------------------------------------------------------- |
| x    | number | No  | No  | Acceleration along the x-axis of the device, in m/s². The value is equal to the reported physical quantity.|
| y    | number | No  | No  | Acceleration along the y-axis of the device, in m/s². The value is equal to the reported physical quantity.|
| z    | number | No  | No  | Acceleration along the z-axis of the device, in m/s². The value is equal to the reported physical quantity.|


## LinearAccelerometerResponse

Describes the linear acceleration sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| x    | number | No  | No  | Linear acceleration along the x-axis of the device, excluding the gravity component, in m/s².|
| y    | number | No  | No  | Linear acceleration along the y-axis of the device, excluding the gravity component, in m/s².|
| z    | number | No  | No  | Linear acceleration along the z-axis of the device, excluding the gravity component, in m/s².|


## AccelerometerUncalibratedResponse

Describes the uncalibrated acceleration sensor data. It is inherited from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name | Type  | Read-Only| Optional| Description                                          |
| ----- | ------ | ---- | ---- | ---------------------------------------------- |
| x     | number | No  | No  | Uncalibrated acceleration along the x-axis of the device, in m/s².    |
| y     | number | No  | No  | Uncalibrated acceleration along the y-axis of the device, in m/s².    |
| z     | number | No  | No  | Uncalibrated acceleration along the z-axis of the device, in m/s².    |
| biasX | number | No  | No  | Uncalibrated acceleration bias (estimated acceleration bias) along the x-axis of the device, in m/s².|
| biasY | number | No  | No  | Uncalibrated acceleration bias (estimated acceleration bias) along the y-axis of the device, in m/s².|
| biasZ | number | No  | No  | Uncalibrated acceleration bias (estimated acceleration bias) along the z-axis of the device, in m/s².|


## FusionPressureResponse<sup>22+</sup>

Describes the fusion pressure sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor

| Name           | Type  | Read-Only| Optional| Description                                          |
| -------------- | ------ | ---- | ---- | ---------------------------------------------- |
| fusionPressure | number | No  | No  | Fused pressure, indicating the percentage of the pressure value applied to the fused pressure sensor, in percentage.    |


## GravityResponse

Describes the gravity sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| x    | number | No  | No  | Gravity acceleration along the x-axis of the device, in m/s².|
| y    | number | No  | No  | Gravity acceleration along the y-axis of the device, in m/s².|
| z    | number | No  | No  | Gravity acceleration along the z-axis of the device, in m/s².|


## OrientationResponse

Describes the orientation sensor data. It extends from [Response](#response).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor


| Name | Type  | Read-Only| Optional| Description                                                 |
| ----- | ------ | ---- | ---- | ----------------------------------------------------- |
| alpha | number | No  | No  | Rotation angle of the device around the z-axis, that is, the yaw angle, in degrees. The value range is [0, 360]. |
| beta  | number | No  | No  | Rotation angle of the device around the x-axis, that is, the pitch angle, in degrees. The value range is [–180, 180].|
| gamma | number | No  | No  | Rotation angle of the device around the y-axis, that is, the roll angle, in degrees. The value range is [–90, 90]. |


## RotationVectorResponse

Describes the rotation vector sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name| Type  | Read-Only| Optional| Description             |
| ---- | ------ | ---- | ---- | ----------------- |
| x    | number | No  | No  | X-axis component of the rotation vector, indicating the projection of the device rotation status on the X axis.|
| y    | number | No  | No  | Y-axis component of the rotation vector, indicating the projection of the device rotation status on the Y axis.|
| z    | number | No  | No  | Z-axis component of the rotation vector, indicating the projection of the device rotation status on the z-axis.|
| w    | number | No  | No  | Scalar component of the rotation vector, which describes the rotation status of the device relative to a reference direction. Unit: radian.           |


## GyroscopeResponse

Describes the gyroscope sensor data. It extends from [Response](#response).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor


| Name| Type  | Read-Only| Optional| Description                                                  |
| ---- | ------ | ---- | ---- | ------------------------------------------------------ |
| x    | number | No  | No  | Rotational angular velocity of the x-axis. in rad/s. The value is equal to the reported physical quantity.|
| y    | number | No  | No  | Rotational angular velocity of the y-axis. in rad/s. The value is equal to the reported physical quantity.|
| z    | number | No  | No  | Rotational angular velocity of the z-axis. in rad/s. The value is equal to the reported physical quantity.|


## GyroscopeUncalibratedResponse

Describes the uncalibrated gyroscope sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name | Type  | Read-Only| Optional| Description                                      |
| ----- | ------ | ---- | ---- | ------------------------------------------ |
| x     | number | No  | No  | Uncalibrated rotational angular velocity of the x-axis, in rad/s.    |
| y     | number | No  | No  | Uncalibrated rotational angular velocity of the y-axis, in rad/s.    |
| z     | number | No  | No  | Uncalibrated rotational angular velocity of the z-axis, in rad/s.    |
| biasX | number | No  | No  | Uncalibrated rotational angular velocity bias (estimated angular velocity bias) of the x-axis, in rad/s.|
| biasY | number | No  | No  | Uncalibrated rotational angular velocity bias (estimated angular velocity bias) along the y-axis of the device, in rad/s.|
| biasZ | number | No  | No  | Uncalibrated rotational angular velocity bias (estimated angular velocity bias) along the z-axis of the device, in rad/s.|


## SignificantMotionResponse

Describes the significant motion sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name  | Type  | Read-Only| Optional| Description                                                        |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| scalar | number | No  | No  | Intensity of a motion. Value range: **1** indicates that a valid motion is detected. The value **1** is reported when the device has a large motion on three physical axes (x, y, and z).|


## ProximityResponse

Describes the proximity sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name    | Type  | Read-Only| Optional| Description                                                      |
| -------- | ------ | ---- | ---- | ---------------------------------------------------------- |
| distance | number | No  | No  | Proximity between the visible object and the device monitor. Value range: **0** indicates that the object is close to the device, and a value greater than 0 indicates that the object is far away from the device.|


## LightResponse

Describes the ambient light sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name                           | Type  | Read-Only| Optional| Description                                                        |
| ------------------------------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| intensity                       | number | No  | No  | Ambient light intensity, in lux.                                      |
| colorTemperature<sup>12+</sup>  | number | No  | Yes  | Color temperature, in K (Kelvin). This parameter is optional. If this parameter is not supported, a fixed value (customized by the sensor) is returned. If this parameter is supported, a normal value is returned.|
| infraredLuminance<sup>12+</sup> | number | No  | Yes  | Infrared luminance. in cd/m². This parameter is optional. If this parameter is not supported, a fixed value (customized by the sensor) is returned. If this parameter is supported, a normal value is returned.|


## HallResponse

Describes the Hall effect sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name  | Type  | Read-Only| Optional| Description                                                        |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| status | number | No  | No  | Hall effect status, indicating whether there is a magnetic force around the device. The value **0** indicates there is no magnetic force, and the Hall effect is off. A value greater than 0 indicates there is magnetic force, and the Hall effect is on.|


## MagneticFieldResponse

Describes the magnetic field sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name| Type  | Read-Only| Optional| Description                        |
| ---- | ------ | ---- | ---- | ---------------------------- |
| x    | number | No  | No  | Magnetic field strength along the x-axis, in μT.|
| y    | number | No  | No  | Magnetic field strength along the y-axis, in μT.|
| z    | number | No  | No  | Magnetic field strength along the z-axis, in μT.|


## MagneticFieldUncalibratedResponse

Describes the uncalibrated magnetic field sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name | Type  | Read-Only| Optional| Description                                  |
| ----- | ------ | ---- | ---- | -------------------------------------- |
| x     | number | No  | No  | Uncalibrated magnetic field strength along the x-axis, in μT.    |
| y     | number | No  | No  | Uncalibrated magnetic field strength along the y-axis, in μT.    |
| z     | number | No  | No  | Uncalibrated magnetic field strength along the z-axis, in μT.    |
| biasX | number | No  | No  | Uncalibrated magnetic field strength bias along the x-axis (estimated magnetic field deviation), in μT.|
| biasY | number | No  | No  | Uncalibrated magnetic field strength bias along the y-axis (estimated magnetic field deviation), in μT.|
| biasZ | number | No  | No  | Uncalibrated magnetic field strength bias along the z-axis (estimated magnetic field deviation), in μT.|


## PedometerResponse

Describes the pedometer sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name | Type  | Read-Only| Optional| Description            |
| ----- | ------ | ---- | ---- | ---------------- |
| steps | number | No  | No  | Number of steps a user has walked. Unit: step|


## HumidityResponse

Describes the humidity sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name    | Type  | Read-Only| Optional| Description                                                     |
| -------- | ------ | ---- | ---- | --------------------------------------------------------- |
| humidity | number | No  | No  | Relative humidity of the environment, in percentage, indicating the relative humidity percentage of the environment.|


## PedometerDetectionResponse

Describes the pedometer detection sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name  | Type  | Read-Only| Optional| Description                                                        |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| scalar | number | No  | No  | Pedometer detection scalar. The value can be **1** (a step counting event is detected, indicating that the user is walking) or **0** (no step counting event is detected, indicating that the user is not moving).|


## AmbientTemperatureResponse

Describes the ambient temperature sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name       | Type  | Read-Only| Optional| Description                      |
| ----------- | ------ | ---- | ---- | -------------------------- |
| temperature | number | No  | No  | Ambient temperature, in °C.|


## BarometerResponse

Describes the barometer sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name    | Type  | Read-Only| Optional| Description                  |
| -------- | ------ | ---- | ---- | ---------------------- |
| pressure | number | No  | No  | Atmospheric pressure, in hPa.|


## HeartRateResponse

Describes the heart rate sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name     | Type  | Read-Only| Optional| Description                                   |
| --------- | ------ | ---- | ---- | --------------------------------------- |
| heartRate | number | No  | No  | Heart rate of a user, in bpm.|


## WearDetectionResponse

Describes the wear detection sensor data. It extends from [Response](#response).

**System capability**: SystemCapability.Sensors.Sensor


| Name | Type  | Read-Only| Optional| Description                                            |
| ----- | ------ | ---- | ---- | ------------------------------------------------ |
| value | number | No  | No  | Device wear status. The value can be **0** (not worn) or **1** (worn).|


## Options

Sets the sensor reporting frequency and sensor selection parameters.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor

| Name    | Type                                                       | Read-Only| Optional| Description                                                                                        |
| -------- | ----------------------------------------------------------- | ---- | ---- |--------------------------------------------------------------------------------------------|
| interval | number\|[SensorFrequency](#sensorfrequency11)<sup>11+</sup> | No  | Yes  | Sets the interval for reporting sensor data. Default value: 200,000,000 ns (200 ms) Unit: ns. For details about the value range, see the **minSamplePeriod** and **maxSamplePeriod** of each sensor. You can query the value range by calling [getSingleSensor](#sensorgetsinglesensor9). You are advised to set a proper reporting frequency based on service requirements. A smaller value indicates more frequent reporting. If the configured frequency is greater than the maximum value, the maximum value is used for data reporting. If the configured frequency is less than the minimum value, the minimum value is used for data reporting.|
| sensorInfoParam<sup>19+</sup> | [SensorInfoParam](#sensorinfoparam19) | No| Yes| The sensor transfers the settings parameter, which can specify **deviceId** and **sensorIndex** to select the target sensor in multi-sensor scenarios.<br>**Atomic service API**: This API can be used in atomic services since API version 19.                                                        |

## SensorFrequency<sup>11+</sup>

type SensorFrequency = 'game' | 'ui' | 'normal'

Defines the sensor reporting frequency modes. The predefined frequency levels are provided, allowing you to quickly set the reporting frequency.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Sensors.Sensor

| Type    | Description                                                        |
| -------- | ------------------------------------------------------------ |
| 'game'   | Game mode, which specifies a sensor data reporting frequency of 20,000,000 ns. This mode is applicable to game apps that are sensitive to data delay. This parameter takes effect only when the frequency is within the frequency range supported by the hardware.|
| 'ui'     | UI mode, which specifies a sensor data reporting frequency of 60,000,000 ns. This mode is applicable to UI interaction apps that have moderate requirements on data update. This parameter takes effect only when the frequency is within the frequency range supported by the hardware.|
| 'normal' | Normal mode, which specifies a sensor data reporting frequency of 200,000,000 ns. This mode is applicable to common apps that do not require high data update frequency. This parameter takes effect only when the frequency is within the frequency range supported by the hardware.|

## RotationMatrixResponse

Response object for setting the rotation matrix, which describes the calculation results of the rotation matrix and tilt matrix.

**System capability**: SystemCapability.Sensors.Sensor

| Name       | Type               | Read-Only| Optional| Description      |
| ----------- | ------------------- | ---- | ---- | ---------- |
| rotation    | Array&lt;number&gt; | No  | No  | Rotation matrix, which is a one-dimensional array with a length of 9, indicating the rotation status of the device in three-dimensional space.|
| inclination | Array&lt;number&gt; | No  | No  | Tilt matrix, which is a one-dimensional array with a length of 9 and indicates the geomagnetic tilt transformation matrix.|


## CoordinatesOptions

Coordinate option object, which is used to specify the transformation direction of the coordinate system.

**System capability**: SystemCapability.Sensors.Sensor

| Name| Type  | Read-Only| Optional| Description       |
| ---- | ------ | ---- | ---- | ----------- |
| x    | number | No  | No  | X coordinate direction, which is used to specify the direction of the rotation matrix transformation on the X axis.|
| y    | number | No  | No  | Y coordinate direction, which is used to specify the direction of the rotation matrix transformation on the Y axis.|


## GeomagneticResponse

Sets the geomagnetic response object, which describes the geomagnetic field information of a specified geographical location.

**System capability**: SystemCapability.Sensors.Sensor

| Name           | Type  | Read-Only| Optional| Description                                              |
| --------------- | ------ | ---- | ---- | -------------------------------------------------- |
| x               | number | No  | No  | X component (north component) of the geomagnetic field, in nT.                                  |
| y               | number | No  | No  | Y component (east component) of the geomagnetic field, in nT.                                  |
| z               | number | No  | No  | Z component (vertical component) of the geomagnetic field, in nT.                                |
| geomagneticDip  | number | No  | No  | Magnetic dip, also called magnetic inclination, which is the angle measured from the horizontal plane to the magnetic field vector, in degrees.            |
| deflectionAngle | number | No  | No  | Magnetic declination, which is the angle between true north (geographic north) and the magnetic north (the horizontal component of the field). in degrees.|
| levelIntensity  | number | No  | No  | Horizontal magnetic field strength, which is the total strength of the geomagnetic field on the horizontal plane. in nT.                                |
| totalIntensity  | number | No  | No  | Total intensity of the geomagnetic field vector in three-dimensional space. in nT.                                  |

## LocationOptions

Indicates the geographical location, which is used to pass the longitude, latitude, and altitude information for calculating the geomagnetic field.

**System capability**: SystemCapability.Sensors.Sensor

| Name     | Type  | Read-Only| Optional| Description      |
| --------- | ------ | ---- | ---- | ---------- |
| latitude  | number | No  | No  | Latitude. Value range: [-90, 90]. Unit: degree    |
| longitude | number | No  | No  | Longitude. Value range: [-180, 180]. Unit: degree    |
| altitude  | number | No  | No  | Altitude. Unit: m|

## sensor.on('SensorType.SENSOR_TYPE_ID_ACCELEROMETER')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;,options?: Options): void

Subscribes to data changes of the acceleration sensor. This API uses an asynchronous callback to return the result. This sensor is applicable to scenarios where the device motion status needs to be detected, such as screen rotation and game control. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.ACCELEROMETER](#sensoronsensoridaccelerometer9) instead.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ACCELEROMETER**.    |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | Yes  | Callback used to return the acceleration sensor data. The reported data type in the callback is **AccelerometerResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

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

## sensor.on('SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION,callback:Callback&lt;LinearAccelerometerResponse&gt;, options?: Options): void

Subscribes to data changes of the linear acceleration sensor. This API uses an asynchronous callback to return the result. This API applies to scenarios where you need to obtain the linear acceleration data excluding the effect of gravity. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.LINEAR_ACCELEROMETER](#sensoronsensoridlinear_accelerometer9) instead.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_LINEAR_ACCELERATION | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_LINEAR_ACCELERATION**.|
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | Yes  | Callback used to return the linear acceleration sensor data. The reported data type in the callback is **LinearAccelerometerResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

## sensor.on('SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED,callback: Callback&lt;AccelerometerUncalibratedResponse&gt;, options?: Options): void

Subscribes to data changes of the uncalibrated acceleration sensor. This API uses an asynchronous callback to return the result. This API is applicable to scenarios where you need to obtain the raw acceleration data that contains deviation calibration data. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.ACCELEROMETER_UNCALIBRATED](#sensoronsensoridaccelerometer_uncalibrated9) instead.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED**.|
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | Yes  | Callback used to return the uncalibrated acceleration sensor data. The reported data type in the callback is **AccelerometerUncalibratedResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

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

## sensor.on('SensorType.SENSOR_TYPE_ID_GRAVITY')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback&lt;GravityResponse&gt;,options?: Options): void

Subscribes to data changes of the gravity sensor. This API uses an asynchronous callback to return the result. This method is suitable for scenarios where the device gravity direction needs to be detected. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.GRAVITY](#sensoronsensoridgravity9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                      | Mandatory| Description                                                       |
| -------- | ---------------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GRAVITY | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GRAVITY**.           |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt;        | Yes  | Callback used to return the gravity sensor data. The reported data type in the callback is **GravityResponse**.|
| options  | [Options](#options)                                        | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Example**

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

## sensor.on('SensorType.SENSOR_TYPE_ID_GYROSCOPE')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;, options?: Options): void

Subscribes to data changes of the gyroscope sensor. This API uses an asynchronous callback to return the result. This sensor is applicable to scenarios where the device's angular velocity needs to be detected. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.GYROSCOPE](#sensoronsensoridgyroscope9) instead.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GYROSCOPE**.        |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt;      | Yes  | Callback used to return the gyroscope sensor data. The reported data type in the callback is **GyroscopeResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

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

## sensor.on('SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED,callback:Callback&lt;GyroscopeUncalibratedResponse&gt;, options?: Options): void

Subscribes to data changes of the uncalibrated gyroscope sensor. This API uses an asynchronous callback to return the result. This method is applicable to scenarios where you need to obtain the raw gyroscope data that contains bias calibration data. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.GYROSCOPE_UNCALIBRATED](#sensoronsensoridgyroscope_uncalibrated9) instead.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED**.|
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | Yes  | Callback used to return the uncalibrated gyroscope sensor data. The reported data type in the callback is **GyroscopeUncalibratedResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

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

## sensor.on('SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;, options?: Options): void

Subscribes to data changes of the significant motion sensor. This API uses an asynchronous callback to return the result. This API is applicable to scenarios where you need to detect whether the device has significant motion. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.SIGNIFICANT_MOTION](#sensoronsensoridsignificant_motion9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_SIGNIFICANT_MOTION | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_SIGNIFICANT_MOTION**.|
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | Yes  | Callback used to return the significant motion sensor data. The reported data type in the callback is **SignificantMotionResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, (data: sensor.SignificantMotionResponse) => {
  console.info('Succeeded in invoking on. Scalar data: ' + data.scalar);
},
  { interval: 100000000 }
);
```

## sensor.on('SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback: Callback&lt;PedometerDetectionResponse&gt;, options?: Options): void

Subscribes to data changes of the pedometer detection sensor. This API uses an asynchronous callback to return the result. This method is suitable for scenarios where you need to detect whether a user is walking. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.PEDOMETER_DETECTION](#sensoronsensoridpedometer_detection9) instead.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER_DETECTION | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PEDOMETER_DETECTION**.|
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | Yes  | Callback used to return the pedometer detection sensor data. The reported data type in the callback is **PedometerDetectionResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
  console.info('Succeeded in invoking on. Scalar data: ' + data.scalar);
},
  { interval: 100000000 }
);
```

## sensor.on('SensorType.SENSOR_TYPE_ID_PEDOMETER')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback&lt;PedometerResponse&gt;, options?: Options): void

Subscribes to data changes of the pedometer sensor. This API uses an asynchronous callback to return the result. This method is suitable for scenarios where the user's step count needs to be obtained. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.PEDOMETER](#sensoronsensoridpedometer9) instead.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PEDOMETER**.          |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt;      | Yes  | Callback used to return the pedometer sensor data. The reported data type in the callback is **PedometerResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER, (data: sensor.PedometerResponse) => {
  console.info('Succeeded in invoking on. Steps: ' + data.steps);
},
  { interval: 100000000 }
);
```

## sensor.on('SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback:Callback&lt;AmbientTemperatureResponse&gt;,  options?: Options): void

Subscribes to data changes of the ambient temperature sensor. This API uses an asynchronous callback to return the result. This method is suitable for scenarios where the ambient temperature needs to be detected. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.AMBIENT_TEMPERATURE](#sensoronsensoridambient_temperature9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_TEMPERATURE | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_AMBIENT_TEMPERATURE**.|
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | Yes  | Callback used to return the ambient temperature sensor data. The reported data type in the callback is **AmbientTemperatureResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
  console.info('Succeeded in invoking on. Temperature: ' + data.temperature);
},
  { interval: 100000000 }
);
```

## sensor.on('SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;,options?: Options): void

Subscribes to data changes of the magnetic field sensor. This API uses an asynchronous callback to return the result. This sensor is applicable to scenarios where the strength and direction of the magnetic field around the device need to be detected. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.MAGNETIC_FIELD](#sensoronsensoridmagnetic_field9) instead. 

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_MAGNETIC_FIELD**.     |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | Yes  | Callback used to return the magnetic field sensor data. The reported data type in the callback is **MagneticFieldResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

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

## sensor.on('SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;, options?: Options): void

Subscribes to data changes of the uncalibrated magnetic field sensor. This API uses an asynchronous callback to return the result. This method applies to scenarios where you need to obtain the raw magnetic field data that contains the deviation calibration data. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.MAGNETIC_FIELD_UNCALIBRATED](#sensoronsensoridmagnetic_field_uncalibrated9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED**.|
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | Yes  | Callback used to return the uncalibrated magnetic field sensor data. The reported data type in the callback is **MagneticFieldUncalibratedResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

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

## sensor.on('SensorType.SENSOR_TYPE_ID_PROXIMITY')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback&lt;ProximityResponse&gt;,options?: Options): void

Subscribes to data changes of the proximity sensor. This API uses an asynchronous callback to return the result. This sensor is applicable to scenarios where the proximity of an object to the device needs to be detected. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.PROXIMITY](#sensoronsensoridproximity9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PROXIMITY | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PROXIMITY**.        |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt;      | Yes  | Callback used to return the proximity sensor data. The reported data type in the callback is **ProximityResponse**.|
| options  | [Options](#options)                                          | No  | Optional parameters used to set the reporting frequency of the sensor when the proximity sensor is frequently triggered. The default value is 200,000,000 ns (200 ms).|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PROXIMITY, (data: sensor.ProximityResponse) => {
  console.info('Succeeded in invoking on. Distance: ' + data.distance);
},
  { interval: 100000000 }
);
```

## sensor.on('SensorType.SENSOR_TYPE_ID_HUMIDITY')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback&lt;HumidityResponse&gt;,options?: Options): void

Subscribes to data changes of the humidity sensor. This API uses an asynchronous callback to return the result. This method is suitable for scenarios where the ambient humidity needs to be detected. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.HUMIDITY](#sensoronsensoridhumidity9) instead. 

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HUMIDITY | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HUMIDITY**.           |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt;       | Yes  | Callback used to return the humidity sensor data. The reported data type in the callback is **HumidityResponse**.|
| options  | [Options](#options)                                         | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_HUMIDITY, (data: sensor.HumidityResponse) => {
  console.info('Succeeded in invoking on. Humidity: ' + data.humidity);
},
  { interval: 100000000 }
);
```

## sensor.on('SensorType.SENSOR_TYPE_ID_BAROMETER')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback&lt;BarometerResponse&gt;,options?: Options): void

Subscribes to data changes of the barometer sensor. This API uses an asynchronous callback to return the result. This method is suitable for scenarios where the ambient barometric pressure needs to be detected. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.BAROMETER](#sensoronsensoridbarometer9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_BAROMETER | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_BAROMETER**.        |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt;      | Yes  | Callback used to return the barometer sensor data. The reported data type in the callback is **BarometerResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_BAROMETER, (data: sensor.BarometerResponse) => {
  console.info('Succeeded in invoking on. Atmospheric pressure: ' + data.pressure);
},
  { interval: 100000000 }
);
```

## sensor.on('SensorType.SENSOR_TYPE_ID_HALL')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback&lt;HallResponse&gt;, options?: Options): void

Subscribes to data changes of the Hall effect sensor. This API uses an asynchronous callback to return the result. This API is applicable to scenarios where the device cover or magnet status needs to be detected. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.HALL](#sensoronsensoridhall9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HALL | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HALL**.               |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt;           | Yes  | Callback used to return the Hall effect sensor data. The reported data type in the callback is **HallResponse**.|
| options  | [Options](#options)                                     | No  | Optional parameters used to set the reporting frequency of the sensor when the Hall effect sensor is frequently triggered. The default value is 200,000,000 ns (200 ms).|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_HALL, (data: sensor.HallResponse) => {
  console.info('Succeeded in invoking on. Status: ' + data.status);
},
  { interval: 100000000 }
);
```

## sensor.on('SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;, options?: Options): void

Subscribes to data changes of the ambient light sensor. This API uses an asynchronous callback to return the result. This API is applicable to scenarios where the ambient light intensity needs to be detected. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.AMBIENT_LIGHT](#sensoronsensoridambient_light9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_LIGHT | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_AMBIENT_LIGHT**.   |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt;              | Yes  | Callback used to return the ambient light sensor data. The reported data type in the callback is **LightResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms).|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, (data: sensor.LightResponse) => {
  console.info('Succeeded in invoking on. Illumination: ' + data.intensity);
},
  { interval: 100000000 }
);
```

## sensor.on('SensorType.SENSOR_TYPE_ID_ORIENTATION')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback&lt;OrientationResponse&gt;, options?: Options): void

Subscribes to data changes of the orientation sensor. This API uses an asynchronous callback to return the result. This method is suitable for scenarios where the device orientation needs to be detected. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.ORIENTATION](#sensoronsensoridorientation9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ORIENTATION | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ORIENTATION**.        |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt;  | Yes  | Callback used to return the orientation sensor data. The reported data type in the callback is **OrientationResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

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

## sensor.on('SensorType.SENSOR_TYPE_ID_HEART_RATE')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;, options?: Options): void

Subscribes to data changes of the heart rate sensor. This API uses an asynchronous callback to return the result. This method is suitable for scenarios where the user's heart rate data needs to be obtained. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.HEART_RATE](#sensoronsensoridheart_rate9) instead.

**Required permissions**: ohos.permission.HEALTH_DATA

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HEART_RATE | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HEART_RATE**.         |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt;      | Yes  | Callback used to return the heart rate sensor data. The reported data type in the callback is **HeartRateResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

## sensor.on('SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;,options?: Options): void

Subscribes to data changes of the rotation vector sensor. This API uses an asynchronous callback to return the result. This sensor is applicable to scenarios where the device rotation status in three-dimensional space needs to be detected. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.ROTATION_VECTOR](#sensoronsensoridrotation_vector9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ROTATION_VECTOR | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ROTATION_VECTOR**.|
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | Yes  | Callback used to return the rotation vector sensor data. The reported data type in the callback is **RotationVectorResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

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

## sensor.on('SensorType.SENSOR_TYPE_ID_WEAR_DETECTION')<sup>(deprecated)</sup>

on(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;,options?: Options): void

Subscribes to data changes of the wear detection sensor. This API uses an asynchronous callback to return the result. This method is suitable for scenarios where you need to check whether a device is being worn. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.on.WEAR_DETECTION](#sensoronsensoridwear_detection9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_WEAR_DETECTION | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_WEAR_DETECTION**. |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | Yes  | Callback used to return the wear detection sensor data. The reported data type in the callback is **WearDetectionResponse**.|
| options  | [Options](#options)                                          | No  | This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns (200 ms). |

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, (data: sensor.WearDetectionResponse) => {
  console.info('Succeeded in invoking on. Wear status: ' + data.value);
},
  { interval: 100000000 }
);
```


## sensor.once('SensorType.SENSOR_TYPE_ID_ACCELEROMETER')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;): void

Subscribes to only one data change of the acceleration sensor. This method applies to scenarios where only the current acceleration data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.ACCELEROMETER](#sensoroncesensoridaccelerometer9) instead.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ACCELEROMETER**.            |
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | Yes  | One-shot callback used to return the acceleration sensor data. The reported data type in the callback is **AccelerometerResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER, (data: sensor.AccelerometerResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback:Callback&lt;LinearAccelerometerResponse&gt;): void

Subscribes to only one data change of the linear acceleration sensor. This method applies to scenarios where only the current linear acceleration data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.LINEAR_ACCELEROMETER](#sensoroncesensoridlinear_accelerometer9) instead.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_LINEAR_ACCELERATION | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_LINEAR_ACCELERATION**.  |
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | Yes  | One-shot callback used to return the linear acceleration sensor data. The reported data type in the callback is **LinearAccelerometerResponse**.|

## sensor.once('SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED,callback: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

Subscribes to only one data change of the uncalibrated acceleration sensor. This method applies to scenarios where only the current uncalibrated acceleration data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.ACCELEROMETER_UNCALIBRATED](#sensoroncesensoridaccelerometer_uncalibrated9) instead.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED**.|
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | Yes  | One-shot callback used to return the uncalibrated acceleration sensor data. The reported data type in the callback is **AccelerometerUncalibratedResponse**.|

**Example**

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

## sensor.once('SensorType.SENSOR_TYPE_ID_GRAVITY')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback&lt;GravityResponse&gt;): void

Subscribes to only one data change of the gravity sensor. This method applies to scenarios where only the current gravity data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.GRAVITY](#sensoroncesensoridgravity9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                      | Mandatory| Description                                                        |
| -------- | ---------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GRAVITY | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GRAVITY**.                    |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt;        | Yes  | One-shot callback used to return the gravity sensor data. The reported data type in the callback is **GravityResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_GRAVITY, (data: sensor.GravityResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  });
```

## sensor.once('SensorType.SENSOR_TYPE_ID_GYROSCOPE')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;): void

Subscribes to only one data change of the gyroscope sensor. This method applies to scenarios where only the current gyroscope data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.GYROSCOPE](#sensoroncesensoridgyroscope9) instead.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GYROSCOPE**.                |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt;      | Yes  | One-shot callback used to return the gyroscope sensor data. The reported data type in the callback is **GyroscopeResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE, (data: sensor.GyroscopeResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED,callback: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

Subscribes to only one data change of the uncalibrated gyroscope sensor. This method applies to scenarios where only the current uncalibrated gyroscope data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.GYROSCOPE_UNCALIBRATED](#sensoroncesensoridgyroscope_uncalibrated9) instead.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED**.|
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | Yes  | One-shot callback used to return the uncalibrated gyroscope sensor data. The reported data type in the callback is **GyroscopeUncalibratedResponse**.|

**Example**


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

## sensor.once('SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;): void

Subscribes to only one data change of the significant motion sensor. This method applies to scenarios where only the current significant motion data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.SIGNIFICANT_MOTION](#sensoroncesensoridsignificant_motion9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_SIGNIFICANT_MOTION | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_SIGNIFICANT_MOTION**.     |
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | Yes  | One-shot callback used to return the significant motion sensor data. The reported data type in the callback is **SignificantMotionResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, (data: sensor.SignificantMotionResponse) => {
  console.info('Succeeded in invoking once. Scalar data: ' + data.scalar);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback: Callback&lt;PedometerDetectionResponse&gt;): void

Subscribes to only one data change of the pedometer detection sensor. This method applies to scenarios where only the current pedometer detection data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.PEDOMETER_DETECTION](#sensoroncesensoridpedometer_detection9) instead.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER_DETECTION | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PEDOMETER_DETECTION**.    |
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | Yes  | One-shot callback used to return the pedometer detection sensor data. The reported data type in the callback is **PedometerDetectionResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
  console.info('Succeeded in invoking once. Scalar data: ' + data.scalar);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_PEDOMETER')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback&lt;PedometerResponse&gt;): void

Subscribes to only one data change of the pedometer sensor. This method applies to scenarios where only the current step count data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.PEDOMETER](#sensoroncesensoridpedometer9) instead.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PEDOMETER**.                  |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt;      | Yes  | One-shot callback used to return the pedometer sensor data. The reported data type in the callback is **PedometerResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER, (data: sensor.PedometerResponse) => {
  console.info('Succeeded in invoking once. Steps: ' + data.steps);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback&lt;AmbientTemperatureResponse&gt;): void

Subscribes to only one data change of the ambient temperature sensor. This method applies to scenarios where the current ambient temperature data needs to be obtained only once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.AMBIENT_TEMPERATURE](#sensoroncesensoridambient_temperature9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_TEMPERATURE | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_AMBIENT_TEMPERATURE**.    |
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | Yes  | One-shot callback used to return the ambient temperature sensor data. The reported data type in the callback is **AmbientTemperatureResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
  console.info('Succeeded in invoking once. Temperature: ' + data.temperature);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;): void

Subscribes to only one data change of the magnetic field sensor. This method applies to scenarios where only the current magnetic field data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.MAGNETIC_FIELD](#sensoroncesensoridmagnetic_field9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_MAGNETIC_FIELD**.             |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | Yes  | One-shot callback used to return the magnetic field sensor data. The reported data type in the callback is **MagneticFieldResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, (data: sensor.MagneticFieldResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

Subscribes to only one data change of the uncalibrated magnetic field sensor. This method applies to scenarios where only the current uncalibrated magnetic field data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.MAGNETIC_FIELD_UNCALIBRATED](#sensoroncesensoridmagnetic_field_uncalibrated9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED**.|
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | Yes  | One-shot callback used to return the uncalibrated magnetic field sensor data. The reported data type in the callback is **MagneticFieldUncalibratedResponse**.|

**Example**

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

## sensor.once('SensorType.SENSOR_TYPE_ID_PROXIMITY')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback&lt;ProximityResponse&gt;): void

Subscribes to only one data change of the proximity sensor. This method applies to scenarios where only the current proximity sensor data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.PROXIMITY](#sensoroncesensoridproximity9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PROXIMITY | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PROXIMITY**.                |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt;      | Yes  | One-shot callback used to return the proximity sensor data. The reported data type in the callback is **ProximityResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_PROXIMITY, (data: sensor.ProximityResponse) => {
  console.info('Succeeded in invoking once. Distance: ' + data.distance);
}
);
```

## sensor.once('SensorType.SENSOR_TYPE_ID_HUMIDITY')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback&lt;HumidityResponse&gt;): void

Subscribes to only one data change of the humidity sensor. This method applies to scenarios where only the current humidity data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.HUMIDITY](#sensoroncesensoridhumidity9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HUMIDITY | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HUMIDITY**.                   |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt;       | Yes  | One-shot callback used to return the humidity sensor data. The reported data type in the callback is **HumidityResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_HUMIDITY, (data: sensor.HumidityResponse) => {
  console.info('Succeeded in invoking once. Humidity: ' + data.humidity);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_BAROMETER')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback&lt;BarometerResponse&gt;): void

Subscribes to only one data change of the barometer sensor. This method applies to scenarios where only the current barometric pressure data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.BAROMETER](#sensoroncesensoridbarometer9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_BAROMETER | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_BAROMETER**.                |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt;      | Yes  | One-shot callback used to return the barometer sensor data. The reported data type in the callback is **BarometerResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_BAROMETER, (data: sensor.BarometerResponse) => {
  console.info('Succeeded in invoking once. Atmospheric pressure: ' + data.pressure);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_HALL')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback&lt;HallResponse&gt;): void

Subscribes to only one data change of the Hall effect sensor. This method applies to scenarios where only the current Hall effect sensor data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.HALL](#sensoroncesensoridhall9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HALL | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HALL**.                       |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt;           | Yes  | One-shot callback used to return the Hall effect sensor data. The reported data type in the callback is **HallResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_HALL, (data: sensor.HallResponse) => {
  console.info('Succeeded in invoking once. Status: ' + data.status);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;): void

Subscribes to only one data change of the ambient light sensor. This method applies to scenarios where only the current ambient light data needs to be obtained at a time.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.AMBIENT_LIGHT](#sensoroncesensoridambient_light9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_LIGHT | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_AMBIENT_LIGHT**.            |
| callback | Callback&lt;[LightResponse](#lightresponse)&gt;              | Yes  | One-shot callback used to return the ambient light sensor data. The reported data type in the callback is **LightResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, (data: sensor.LightResponse) => {
  console.info('Succeeded in invoking once. Illumination: ' + data.intensity);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_ORIENTATION')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback&lt;OrientationResponse&gt;): void

Subscribes to only one data change of the orientation sensor. This method applies to scenarios where only the current orientation data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.ORIENTATION](#sensoroncesensoridorientation9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ORIENTATION | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ORIENTATION**.                |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt;  | Yes  | One-shot callback used to return the orientation sensor data. The reported data type in the callback is **OrientationResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_ORIENTATION, (data: sensor.OrientationResponse) => {
  console.info('Succeeded in invoking the device rotating at an angle around the X axis: ' + data.beta);
  console.info('Succeeded in invoking the device rotating at an angle around the Y axis: ' + data.gamma);
  console.info('Succeeded in invoking the device rotating at an angle around the Z axis: ' + data.alpha);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;): void

Subscribes to only one data change of the rotation vector sensor. This method applies to scenarios where only the current rotation vector data needs to be obtained at a time.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.ROTATION_VECTOR](#sensoroncesensoridrotation_vector9) instead. 

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ROTATION_VECTOR | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ROTATION_VECTOR**.        |
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | Yes  | One-shot callback used to return the rotation vector sensor data. The reported data type in the callback is **RotationVectorResponse**.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, (data: sensor.RotationVectorResponse) => {
  console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking once. Scalar quantity: ' + data.w);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_HEART_RATE')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;): void

Subscribes to only one data change of the heart rate sensor. This method applies to scenarios where only the current heart rate data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.HEART_RATE](#sensoroncesensoridheart_rate9) instead.

**Required permissions**: ohos.permission.HEART_RATE 

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HEART_RATE | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HEART_RATE**.                 |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt;      | Yes  | One-shot callback used to return the heart rate sensor data. The reported data type in the callback is **HeartRateResponse**.|

**Example**


```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_HEART_RATE, (data: sensor.HeartRateResponse) => {
  console.info("Succeeded in invoking once. Heart rate: " + data.heartRate);
});
```

## sensor.once('SensorType.SENSOR_TYPE_ID_WEAR_DETECTION')<sup>(deprecated)</sup>

once(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;): void

Subscribes to only one data change of the wear detection sensor. This method applies to scenarios where only the current wear detection data needs to be obtained once.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.once.WEAR_DETECTION](#sensoroncesensoridwear_detection9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_WEAR_DETECTION | Yes  | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_WEAR_DETECTION**.         |
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | Yes  | One-shot callback used to return the wear detection sensor data. The reported data type in the callback is **WearDetectionResponse**.|

**Example**


```ts
import { sensor } from '@kit.SensorServiceKit';

sensor.once(sensor.SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, (data: sensor.WearDetectionResponse) => {
  console.info("Succeeded in invoking once. Wear status: " + data.value);
});
```


## sensor.off('SensorType.SENSOR_TYPE_ID_ACCELEROMETER')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback?: Callback&lt;AccelerometerResponse&gt;): void

Unsubscribes from data of the acceleration sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.ACCELEROMETER](#sensoroffsensoridaccelerometer9) instead.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_ACCELEROMETER**.|
| callback | Callback&lt;[AccelerometerResponse](#accelerometerresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.AccelerometerResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback?: Callback&lt;AccelerometerUncalibratedResponse&gt;): void

Unsubscribes from data of the uncalibrated acceleration sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.ACCELEROMETER_UNCALIBRATED](#sensoroffsensoridaccelerometer_uncalibrated9) instead.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED**.|
| callback | Callback&lt;[AccelerometerUncalibratedResponse](#accelerometeruncalibratedresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

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

## sensor.off('SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback?: Callback&lt;LightResponse&gt;): void

Unsubscribes from data of the ambient light sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.AMBIENT_LIGHT](#sensoroffsensoridambient_light9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_LIGHT | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_AMBIENT_LIGHT**.|
| callback | Callback&lt;[LightResponse](#lightresponse)&gt;              | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.LightResponse) {
  console.info('Succeeded in invoking off. Illumination: ' + data.intensity);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback?: Callback&lt;AmbientTemperatureResponse&gt;): void

Unsubscribes from data of the ambient temperature sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.AMBIENT_TEMPERATURE](#sensoroffsensoridambient_temperature9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_AMBIENT_TEMPERATURE | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_AMBIENT_TEMPERATURE**.|
| callback | Callback&lt;[AmbientTemperatureResponse](#ambienttemperatureresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.AmbientTemperatureResponse) {
  console.info('Succeeded in invoking off. Temperature: ' + data.temperature);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_BAROMETER')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback?: Callback&lt;BarometerResponse&gt;): void

Unsubscribes from data of the barometer sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.BAROMETER](#sensoroffsensoridbarometer9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_BAROMETER | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_BAROMETER**.    |
| callback | Callback&lt;[BarometerResponse](#barometerresponse)&gt;      | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.BarometerResponse) {
  console.info('Succeeded in invoking off. Atmospheric pressure: ' + data.pressure);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_BAROMETER, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_GRAVITY')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback?: Callback&lt;GravityResponse&gt;): void

Unsubscribes from data of the gravity sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.GRAVITY](#sensoroffsensoridgravity9) instead. 

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                      | Mandatory| Description                                                        |
| -------- | ---------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GRAVITY | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_GRAVITY**.        |
| callback | Callback&lt;[GravityResponse](#gravityresponse)&gt;        | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.GravityResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_GRAVITY, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_GYROSCOPE')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback?: Callback&lt;GyroscopeResponse&gt;): void

Unsubscribes from data of the gyroscope sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.GYROSCOPE](#sensoroffsensoridgyroscope9) instead.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_GYROSCOPE**.    |
| callback | Callback&lt;[GyroscopeResponse](#gyroscoperesponse)&gt;      | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.GyroscopeResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback?: Callback&lt;GyroscopeUncalibratedResponse&gt;): void

Unsubscribes from data of the uncalibrated gyroscope sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.GYROSCOPE_UNCALIBRATED](#sensoroffsensoridgyroscope_uncalibrated9) instead.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED**.|
| callback | Callback&lt;[GyroscopeUncalibratedResponse](#gyroscopeuncalibratedresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.GyroscopeUncalibratedResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_HALL')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_HALL, callback?: Callback&lt;HallResponse&gt;): void

Unsubscribes from data of the Hall effect sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.HALL](#sensoroffsensoridhall9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HALL | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_HALL**.           |
| callback | Callback&lt;[HallResponse](#hallresponse)&gt;           | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.HallResponse) {
  console.info('Succeeded in invoking off. Status: ' + data.status);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_HALL, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_HEART_RATE')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback?: Callback&lt;HeartRateResponse&gt;): void

Unsubscribes from data of the heart rate sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.HEART_RATE](#sensoroffsensoridheart_rate9) instead.

**Required permissions**: ohos.permission.HEALTH_DATA

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HEART_RATE | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_HEART_RATE**.     |
| callback | Callback&lt;[HeartRateResponse](#heartrateresponse)&gt;      | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.HeartRateResponse) {
  console.info('Succeeded in invoking off. Heart rate: ' + data.heartRate);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_HEART_RATE, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_HUMIDITY')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback?: Callback&lt;HumidityResponse&gt;): void

Unsubscribes from data of the humidity sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.HUMIDITY](#sensoroffsensoridhumidity9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_HUMIDITY | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_HUMIDITY**.       |
| callback | Callback&lt;[HumidityResponse](#humidityresponse)&gt;       | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.HumidityResponse) {
  console.info('Succeeded in invoking off. Humidity: ' + data.humidity);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_HUMIDITY, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback?: Callback&lt;LinearAccelerometerResponse&gt;): void

Unsubscribes from data of the linear acceleration sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.LINEAR_ACCELEROMETER](#sensoroffsensoridlinear_accelerometer9) instead.

**Required permissions**: ohos.permission.ACCELEROMETER

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_LINEAR_ACCELERATION | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_LINEAR_ACCELERATION**.|
| callback | Callback&lt;[LinearAccelerometerResponse](#linearaccelerometerresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.LinearAccelerometerResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD')<sup>(deprecated)</sup>

 off(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback?: Callback&lt;MagneticFieldResponse&gt;): void

Unsubscribes from data of the magnetic field sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.MAGNETIC_FIELD](#sensoroffsensoridmagnetic_field9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_MAGNETIC_FIELD**. |
| callback | Callback&lt;[MagneticFieldResponse](#magneticfieldresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.MagneticFieldResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED')<sup>(deprecated)</sup>

 off(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback?: Callback&lt;MagneticFieldUncalibratedResponse&gt;): void

Unsubscribes from data of the uncalibrated magnetic field sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.MAGNETIC_FIELD_UNCALIBRATED](#sensoroffsensoridmagnetic_field_uncalibrated9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED**.|
| callback | Callback&lt;[MagneticFieldUncalibratedResponse](#magneticfielduncalibratedresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

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

## sensor.off('SensorType.SENSOR_TYPE_ID_ORIENTATION')<sup>(deprecated)</sup>

 off(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback?: Callback&lt;OrientationResponse&gt;): void

Unsubscribes from data of the orientation sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.ORIENTATION](#sensoroffsensoridorientation9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ORIENTATION | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_ORIENTATION**.    |
| callback | Callback&lt;[OrientationResponse](#orientationresponse)&gt;  | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.OrientationResponse) {
  console.info('Succeeded in invoking off. The device rotates at an angle around the X axis: ' + data.beta);
  console.info('Succeeded in invoking off. The device rotates at an angle around the Y axis: ' + data.gamma);
  console.info('Succeeded in invoking off. The device rotates at an angle around the Z axis: ' + data.alpha);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_ORIENTATION, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_PEDOMETER')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback?: Callback&lt;PedometerResponse&gt;): void

Unsubscribes from data of the pedometer sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.PEDOMETER](#sensoroffsensoridpedometer9) instead.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_PEDOMETER**.      |
| callback | Callback&lt;[PedometerResponse](#pedometerresponse)&gt;      | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.PedometerResponse) {
  console.info('Succeeded in invoking off. Steps: ' + data.steps);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback?: Callback&lt;PedometerDetectionResponse&gt;): void

Unsubscribes from data of the pedometer detection sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.PEDOMETER_DETECTION](#sensoroffsensoridpedometer_detection9) instead.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PEDOMETER_DETECTION | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_PEDOMETER_DETECTION**.|
| callback | Callback&lt;[PedometerDetectionResponse](#pedometerdetectionresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.PedometerDetectionResponse) {
  console.info('Succeeded in invoking off. Scalar data: ' + data.scalar);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_PROXIMITY')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback?: Callback&lt;ProximityResponse&gt;): void

Unsubscribes from data of the proximity sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.PROXIMITY](#sensoroffsensoridproximity9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_PROXIMITY | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_PROXIMITY**.    |
| callback | Callback&lt;[ProximityResponse](#proximityresponse)&gt;      | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.ProximityResponse) {
  console.info('Succeeded in invoking off. Distance: ' + data.distance);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_PROXIMITY, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback?: Callback&lt;RotationVectorResponse&gt;): void

Unsubscribes from data of the rotation vector sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.ROTATION_VECTOR](#sensoroffsensoridrotation_vector9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_ROTATION_VECTOR | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_ROTATION_VECTOR**.|
| callback | Callback&lt;[RotationVectorResponse](#rotationvectorresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

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

## sensor.off('SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback?: Callback&lt;SignificantMotionResponse&gt;): void

Unsubscribes from significant motion sensor data. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.SIGNIFICANT_MOTION](#sensoroffsensoridsignificant_motion9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_SIGNIFICANT_MOTION | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_SIGNIFICANT_MOTION**.|
| callback | Callback&lt;[SignificantMotionResponse](#significantmotionresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.SignificantMotionResponse) {
  console.info('Succeeded in invoking off. Scalar data: ' + data.scalar);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback);
```

## sensor.off('SensorType.SENSOR_TYPE_ID_WEAR_DETECTION')<sup>(deprecated)</sup>

off(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback?: Callback&lt;WearDetectionResponse&gt;): void

Unsubscribes from data of the wear detection sensor. The **off** API for canceling subscription and the **on** API for subscription must be used in pairs.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.off.WEAR_DETECTION](#sensoroffsensoridwear_detection9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | [SensorType](#sensortypedeprecated).SENSOR_TYPE_ID_WEAR_DETECTION | Yes  | Type of the sensor to unsubscribe from, which is **SENSOR_TYPE_ID_WEAR_DETECTION**.|
| callback | Callback&lt;[WearDetectionResponse](#weardetectionresponse)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';

function accCallback(data: sensor.WearDetectionResponse) {
  console.info('Succeeded in invoking off. Wear status: ' + data.value);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, accCallback);
```

## sensor.transformCoordinateSystem<sup>(deprecated)</sup>

transformCoordinateSystem(inRotationVector: Array&lt;number&gt;, coordinates: CoordinatesOptions, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

Rotates a rotation vector so that it can represent the coordinate system in different ways. This API uses an asynchronous callback to return the result. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.transformRotationMatrix](#sensortransformrotationmatrix9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name          | Type                                     | Mandatory| Description                      |
| ---------------- | ----------------------------------------- | ---- | -------------------------- |
| inRotationVector | Array&lt;number&gt;                       | Yes  | Rotation vector.            |
| coordinates      | [CoordinatesOptions](#coordinatesoptions) | Yes  | Direction of the coordinate system.          |
| callback         | AsyncCallback&lt;Array&lt;number&gt;&gt;  | Yes  | Callback used to return the rotation vector after being rotated.|

**Example**

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

Rotates a rotation vector so that it can represent the coordinate system in different ways. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.transformRotationMatrix](#sensortransformrotationmatrix9-1) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name             | Type                                      | Mandatory  | Description      |
| ---------------- | ---------------------------------------- | ---- | -------- |
| inRotationVector | Array&lt;number&gt;                      | Yes   | Rotation vector. |
| coordinates      | [CoordinatesOptions](#coordinatesoptions) | Yes   | Direction of the coordinate system.|

**Return value**

| Type                              | Description                              |
| ---------------------------------- | ---------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation vector after being rotated.|

**Example**

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

Obtains the geomagnetic field of a geographic location. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getGeomagneticInfo](#sensorgetgeomagneticinfo9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name         | Type                                                        | Mandatory| Description                              |
| --------------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| locationOptions | [LocationOptions](#locationoptions)                          | Yes  | Geographic location.                        |
| timeMillis      | number                                                       | Yes  | Time for obtaining the magnetic declination, in milliseconds.|
| callback        | AsyncCallback&lt;[GeomagneticResponse](#geomagneticresponse)&gt; | Yes  | Callback used to return the geomagnetic field.                |

**Example**

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

Obtains the geomagnetic field of a geographic location. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getGeomagneticInfo](#sensorgetgeomagneticinfo9-1) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name            | Type                                 | Mandatory  | Description               |
| --------------- | ----------------------------------- | ---- | ----------------- |
| locationOptions | [LocationOptions](#locationoptions) | Yes   | Geographic location.            |
| timeMillis      | number                              | Yes   | Time for obtaining the magnetic declination, in milliseconds.|

**Return value**

| Type                                                      | Description                      |
| ---------------------------------------------------------- | -------------------------- |
| Promise&lt;[GeomagneticResponse](#geomagneticresponse)&gt; | Promise used to return the geomagnetic field.|

**Example**

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

Obtains the altitude at which the device is located based on the sea-level atmospheric pressure and the current atmospheric pressure. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getDeviceAltitude](#sensorgetdevicealtitude9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name         | Type                       | Mandatory| Description                                  |
| --------------- | --------------------------- | ---- | -------------------------------------- |
| seaPressure     | number                      | Yes  | Sea-level atmospheric pressure, in hPa.         |
| currentPressure | number                      | Yes  | Atmospheric pressure at the altitude where the device is located, in hPa. |
| callback        | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the altitude, in meters.|

**Example**

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

Obtains the altitude at which the device is located based on the sea-level atmospheric pressure and the current atmospheric pressure. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getDeviceAltitude](#sensorgetdevicealtitude9-1) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name            | Type    | Mandatory  | Description                  |
| --------------- | ------ | ---- | -------------------- |
| seaPressure     | number | Yes   | Sea-level atmospheric pressure, in hPa.    |
| currentPressure | number | Yes   | Atmospheric pressure at the altitude where the device is located, in hPa.|

**Return value**

| Type                 | Description                                            |
| --------------------- | ------------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the altitude, in meters.|

**Example**

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

Obtains the magnetic dip based on the inclination matrix. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getInclination](#sensorgetinclination9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name           | Type                       | Mandatory| Description                            |
| ----------------- | --------------------------- | ---- | -------------------------------- |
| inclinationMatrix | Array&lt;number&gt;         | Yes  | Inclination matrix.                  |
| callback          | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the magnetic dip, in radians.|

**Example**

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

Obtains the magnetic dip based on the inclination matrix. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getInclination](#sensorgetinclination9-1) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name              | Type                 | Mandatory  | Description     |
| ----------------- | ------------------- | ---- | ------- |
| inclinationMatrix | Array&lt;number&gt; | Yes   | Inclination matrix.|

**Return value**

| Type                 | Description                                    |
| --------------------- | ---------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the magnetic dip, in radians.|

**Example**

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

Obtains the angle change between two rotation matrices. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getAngleVariation](#sensorgetanglevariation9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name               | Type                                    | Mandatory| Description                                 |
| --------------------- | ---------------------------------------- | ---- | ------------------------------------- |
| currentRotationMatrix | Array&lt;number&gt;                      | Yes  | Current rotation matrix.                   |
| preRotationMatrix     | Array&lt;number&gt;                      | Yes  | The other rotation matrix.                       |
| callback              | AsyncCallback&lt;Array&lt;number&gt;&gt; | Yes  | Asynchronous callback used to return the rotation angle changes around the z, x, and y axes, in degrees (°).|

**Example**

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

Obtains the angle change between two rotation matrices. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getAngleVariation](#sensorgetanglevariation9-1) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name                  | Type                 | Mandatory  | Description       |
| --------------------- | ------------------- | ---- | --------- |
| currentRotationMatrix | Array&lt;number&gt; | Yes   | Current rotation matrix.|
| preRotationMatrix     | Array&lt;number&gt; | Yes   | The other rotation matrix.  |

**Return value**

| Type                              | Description                                         |
| ---------------------------------- | --------------------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation angle changes of the z, x, and y axes, in degrees (°).|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getAngleModify([1, 0, 0, 0, 1, 0, 0, 0, 1], [1, 0, 0, 0, 0.87, -0.50, 0, 0.50, 0.87]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting AngleModify_promise.');
  for (let i = 0; i < data.length; i++) {
    console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
  }
}).catch((reason: BusinessError) => {
  let e: BusinessError = reason as BusinessError;
  console.info('Succeeded in getting promise::catch', e);
})
```

## sensor.createRotationMatrix<sup>(deprecated)</sup>

createRotationMatrix(rotationVector: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

Converts a rotation vector into a rotation matrix. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getRotationMatrix](#sensorgetrotationmatrix9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name        | Type                                    | Mandatory| Description              |
| -------------- | ---------------------------------------- | ---- | ------------------ |
| rotationVector | Array&lt;number&gt;                      | Yes  | Rotation vector to convert.    |
| callback       | AsyncCallback&lt;Array&lt;number&gt;&gt; | Yes  | Callback used to return the rotation matrix.|

**Example**

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

Converts a rotation vector into a rotation matrix. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getRotationMatrix](#sensorgetrotationmatrix9-1) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name           | Type                 | Mandatory  | Description     |
| -------------- | ------------------- | ---- | ------- |
| rotationVector | Array&lt;number&gt; | Yes   | Rotation vector to convert.|

**Return value**

| Type                              | Description                      |
| ---------------------------------- | -------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation matrix.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createRotationMatrix([0.20046076, 0.21907, 0.73978853, 0.60376877]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting createRotationMatrix_promise');
  for (let i = 0; i < data.length; i++) {
    console.info('data[' + i + ']: ' + data[i]);
  }
}).catch((reason: BusinessError) => {
  console.info('Succeeded in getting promise::catch', reason);
})
```

## sensor.createQuaternion<sup>(deprecated)</sup>

createQuaternion(rotationVector: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

Converts a rotation vector into a quaternion. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getQuaternion](#sensorgetquaternion9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name        | Type                                    | Mandatory| Description            |
| -------------- | ---------------------------------------- | ---- | ---------------- |
| rotationVector | Array&lt;number&gt;                      | Yes  | Rotation vector to convert.  |
| callback       | AsyncCallback&lt;Array&lt;number&gt;&gt; | Yes  | Callback used to return the quaternion.|

**Example**

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

Converts a rotation vector into a quaternion. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getQuaternion](#sensorgetquaternion9-1) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name           | Type                 | Mandatory  | Description     |
| -------------- | ------------------- | ---- | ------- |
| rotationVector | Array&lt;number&gt; | Yes   | Rotation vector to convert.|

**Return value**

| Type                              | Description                    |
| ---------------------------------- | ------------------------ |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the quaternion.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createQuaternion([0.20046076, 0.21907, 0.73978853, 0.60376877]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting createQuaternion_promise');
  for (let i = 0; i < data.length; i++) {
    console.info('data[' + i + ']: ' + data[i]);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get promise.`);
})
```

## sensor.getDirection<sup>(deprecated)</sup>

getDirection(rotationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

Obtains the device direction based on the rotation matrix. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getOrientation](#sensorgetorientation9) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name        | Type                                    | Mandatory| Description                                 |
| -------------- | ---------------------------------------- | ---- | ------------------------------------- |
| rotationMatrix | Array&lt;number&gt;                      | Yes  | The other rotation matrix.                       |
| callback       | AsyncCallback&lt;Array&lt;number&gt;&gt; | Yes  | Asynchronous callback used to return the rotation angles around the z, x, and y axes, in degrees (°).|

**Example**

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

Obtains the device direction based on the rotation matrix. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getOrientation](#sensorgetorientation9-1) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name           | Type                 | Mandatory  | Description     |
| -------------- | ------------------- | ---- | ------- |
| rotationMatrix | Array&lt;number&gt; | Yes   | The other rotation matrix.|

**Return value**

| Type                              | Description                                         |
| ---------------------------------- | --------------------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation angles around the z, x, and y axes, in degrees (°).|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getDirection([1, 0, 0, 0, 1, 0, 0, 0, 1]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting sensor_getDirection_Promise', data);
  for (let i = 1; i < data.length; i++) {
    console.info('Succeeded in getting sensor_getDirection_promise' + data[i]);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get promise.`);
})
```

## sensor.createRotationMatrix<sup>(deprecated)</sup>

createRotationMatrix(gravity: Array&lt;number&gt;, geomagnetic: Array&lt;number&gt;, callback: AsyncCallback&lt;RotationMatrixResponse&gt;): void

Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getRotationMatrix](#sensorgetrotationmatrix9-2) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name     | Type                                                        | Mandatory| Description              |
| ----------- | ------------------------------------------------------------ | ---- | ------------------ |
| gravity     | Array&lt;number&gt;                                          | Yes  | Gravity vector.    |
| geomagnetic | Array&lt;number&gt;                                          | Yes  | Geomagnetic vector.    |
| callback    | AsyncCallback&lt;[RotationMatrixResponse](#rotationmatrixresponse)&gt; | Yes  | Callback used to return the rotation matrix.|

**Example**

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

Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.getRotationMatrix](#sensorgetrotationmatrix9-3) instead.

**System capability**: SystemCapability.Sensors.Sensor

**Parameters**

| Name        | Type                 | Mandatory  | Description     |
| ----------- | ------------------- | ---- | ------- |
| gravity     | Array&lt;number&gt; | Yes   | Gravity vector.|
| geomagnetic | Array&lt;number&gt; | Yes   | Geomagnetic vector.|

**Return value**

| Type                                                        | Description                      |
| ------------------------------------------------------------ | -------------------------- |
| Promise&lt;[RotationMatrixResponse](#rotationmatrixresponse)&gt; | Promise used to return the rotation matrix.|

**Example**

```ts
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createRotationMatrix([-0.27775216, 0.5351276, 9.788099], [210.87253, -78.6096, -111.44444]);
promise.then((data: sensor.RotationMatrixResponse) => {
  console.info(JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to get promise.`);
})
```

## SensorType<sup>(deprecated)</sup>

Enumerates the sensor types.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [sensor.SensorId](#sensorid9) instead.

**System capability**: SystemCapability.Sensors.Sensor

| Name                                      | Value  | Description                  |
| ------------------------------------------ | ---- | ---------------------- |
| SENSOR_TYPE_ID_ACCELEROMETER               | 1    | Acceleration sensor.        |
| SENSOR_TYPE_ID_GYROSCOPE                   | 2    | Gyroscope sensor.        |
| SENSOR_TYPE_ID_AMBIENT_LIGHT               | 5    | Ambient light sensor.        |
| SENSOR_TYPE_ID_MAGNETIC_FIELD              | 6    | Magnetic field sensor.          |
| SENSOR_TYPE_ID_BAROMETER                   | 8    | Barometer sensor.        |
| SENSOR_TYPE_ID_HALL                        | 10   | Hall effect sensor.          |
| SENSOR_TYPE_ID_PROXIMITY                   | 12   | Proximity sensor.        |
| SENSOR_TYPE_ID_HUMIDITY                    | 13   | Humidity sensor.          |
| SENSOR_TYPE_ID_ORIENTATION                 | 256  | Orientation sensor.          |
| SENSOR_TYPE_ID_GRAVITY                     | 257  | Gravity sensor.          |
| SENSOR_TYPE_ID_LINEAR_ACCELERATION         | 258  | Linear acceleration sensor.    |
| SENSOR_TYPE_ID_ROTATION_VECTOR             | 259  | Rotation vector sensor.      |
| SENSOR_TYPE_ID_AMBIENT_TEMPERATURE         | 260  | Ambient temperature sensor.      |
| SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | 261  | Uncalibrated magnetic field sensor.    |
| SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED      | 263  | Uncalibrated gyroscope sensor.  |
| SENSOR_TYPE_ID_SIGNIFICANT_MOTION          | 264  | Significant motion sensor.      |
| SENSOR_TYPE_ID_PEDOMETER_DETECTION         | 265  | Pedometer detection sensor.      |
| SENSOR_TYPE_ID_PEDOMETER                   | 266  | Pedometer sensor.          |
| SENSOR_TYPE_ID_HEART_RATE                  | 278  | Heart rate sensor.          |
| SENSOR_TYPE_ID_WEAR_DETECTION              | 280  | Wear detection sensor.      |
| SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED  | 281  | Uncalibrated acceleration sensor.|
