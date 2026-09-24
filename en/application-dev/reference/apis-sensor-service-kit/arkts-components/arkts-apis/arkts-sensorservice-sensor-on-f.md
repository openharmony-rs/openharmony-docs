# on

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

<a id="on-2"></a>

## on

```TypeScript
function on(type: SensorId.ACCELEROMETER, callback: Callback<AccelerometerResponse>,
    options?: Options): void
```

Subscribes to data of the acceleration sensor.

**Since:** 9

**Required permissions:** ohos.permission.ACCELEROMETER

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.ACCELEROMETER](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.ACCELEROMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerResponse](arkts-sensorservice-sensor-accelerometerresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is an **AccelerometerResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-3"></a>

## on

```TypeScript
function on(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback<AccelerometerUncalibratedResponse>,
    options?: Options): void
```

Subscribes to data of the uncalibrated acceleration sensor.

**Since:** 9

**Required permissions:** ohos.permission.ACCELEROMETER

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.ACCELEROMETER_UNCALIBRATED](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.ACCELEROMETER_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is an **AccelerometerUncalibratedResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-4"></a>

## on

```TypeScript
function on(type: SensorId.AMBIENT_LIGHT, callback: Callback<LightResponse>, options?: Options): void
```

Subscribes to data of the ambient light sensor.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.AMBIENT_LIGHT](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.AMBIENT_LIGHT**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LightResponse](arkts-sensorservice-sensor-lightresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **LightResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-5"></a>

## on

```TypeScript
function on(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback<AmbientTemperatureResponse>,
    options?: Options): void
```

Subscribes to data of the ambient temperature sensor.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.AMBIENT_TEMPERATURE](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.AMBIENT_TEMPERATURE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is an **AmbientTemperatureResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-6"></a>

## on

```TypeScript
function on(type: SensorId.BAROMETER, callback: Callback<BarometerResponse>, options?: Options): void
```

Subscribes to data of the barometer sensor.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.BAROMETER](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.BAROMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BarometerResponse](arkts-sensorservice-sensor-barometerresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **BarometerResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-7"></a>

## on

```TypeScript
function on(type: SensorId.GRAVITY, callback: Callback<GravityResponse>,
    options?: Options): void
```

Subscribes to data of the gravity sensor.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.GRAVITY](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.GRAVITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **GravityResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-8"></a>

## on

```TypeScript
function on(type: SensorId.GYROSCOPE, callback: Callback<GyroscopeResponse>,
    options?: Options): void
```

Subscribes to data of the gyroscope sensor.

**Since:** 9

**Required permissions:** ohos.permission.GYROSCOPE

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.GYROSCOPE](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.GYROSCOPE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeResponse](arkts-sensorservice-sensor-gyroscoperesponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **GyroscopeResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-9"></a>

## on

```TypeScript
function on(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback<GyroscopeUncalibratedResponse>,
    options?: Options): void
```

Subscribes to data of the uncalibrated gyroscope sensor.

**Since:** 9

**Required permissions:** ohos.permission.GYROSCOPE

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.GYROSCOPE_UNCALIBRATED](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.GYROSCOPE_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **GyroscopeUncalibratedResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-10"></a>

## on

```TypeScript
function on(type: SensorId.HALL, callback: Callback<HallResponse>, options?: Options): void
```

Subscribes to data of the Hall effect sensor.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.HALL](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.HALL**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **HallResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. The default value is 200,000,000 ns. This parameter is used to set the data reporting frequency when Hall effect events are frequently triggered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-11"></a>

## on

```TypeScript
function on(type: SensorId.HEART_RATE, callback: Callback<HeartRateResponse>,
    options?: Options): void
```

Subscribes to data of the heart rate sensor.

**Since:** 9

**Required permissions:** ohos.permission.READ_HEALTH_DATA

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.HEART_RATE](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.HEART_RATE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HeartRateResponse](arkts-sensorservice-sensor-heartrateresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **HeartRateResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-12"></a>

## on

```TypeScript
function on(type: SensorId.HUMIDITY, callback: Callback<HumidityResponse>,
    options?: Options): void
```

Subscribes to data of the humidity sensor.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.HUMIDITY](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.HUMIDITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **HumidityResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-13"></a>

## on

```TypeScript
function on(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback<LinearAccelerometerResponse>,
    options?: Options): void
```

Subscribes to data of the linear acceleration sensor.

**Since:** 9

**Required permissions:** ohos.permission.ACCELEROMETER

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.LINEAR_ACCELEROMETER](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.LINEAR_ACCELEROMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **LinearAccelerometerResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-14"></a>

## on

```TypeScript
function on(type: SensorId.MAGNETIC_FIELD, callback: Callback<MagneticFieldResponse>,
    options?: Options): void
```

Subscribes to data of the magnetic field sensor.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.MAGNETIC_FIELD](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **MagneticFieldResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-15"></a>

## on

```TypeScript
function on(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback<MagneticFieldUncalibratedResponse>,
    options?: Options): void
```

Subscribes to data of the uncalibrated magnetic field sensor.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.MAGNETIC_FIELD_UNCALIBRATED](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **MagneticFieldUncalibratedResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-16"></a>

## on

```TypeScript
function on(type: SensorId.ORIENTATION, callback: Callback<OrientationResponse>,
    options?: Options): void
```

Subscribes to data of the orientation sensor.

> **NOTE:** 
> 
> Applications or services invoking this API can prompt users to use figure-8 calibration to improve the accuracy
> of the direction sensor. The sensor has a theoretical error of ±5 degrees, but the specific precision may vary
> depending on different driver implementations and algorithmic designs.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.ORIENTATION](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.ORIENTATION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **OrientationResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-17"></a>

## on

```TypeScript
function on(type: SensorId.PEDOMETER, callback: Callback<PedometerResponse>, options?: Options): void
```

Subscribes to data of the pedometer sensor. The step counter sensor's data reporting is subject to some delay, and the delay is determined by specific product implementations.

**Since:** 9

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.PEDOMETER](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.PEDOMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **PedometerResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-18"></a>

## on

```TypeScript
function on(type: SensorId.PEDOMETER_DETECTION, callback: Callback<PedometerDetectionResponse>,
    options?: Options): void
```

Subscribes to data of the pedometer detection sensor.

**Since:** 9

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.PEDOMETER_DETECTION](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.PEDOMETER_DETECTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **PedometerDetectionResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-19"></a>

## on

```TypeScript
function on(type: SensorId.PROXIMITY, callback: Callback<ProximityResponse>, options?: Options): void
```

Subscribes to data of the proximity sensor.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.PROXIMITY](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.PROXIMITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProximityResponse](arkts-sensorservice-sensor-proximityresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **ProximityResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. The default value is 200,000,000 ns. This parameter is used to set the data reporting frequency when proximity sensor events are frequently triggered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-20"></a>

## on

```TypeScript
function on(type: SensorId.ROTATION_VECTOR, callback: Callback<RotationVectorResponse>,
    options?: Options): void
```

Subscribes to data of the rotation vector sensor.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.ROTATION_VECTOR](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.ROTATION_VECTOR**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **RotationVectorResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-21"></a>

## on

```TypeScript
function on(type: SensorId.SIGNIFICANT_MOTION, callback: Callback<SignificantMotionResponse>,
    options?: Options): void
```

Subscribes to the significant motion sensor data.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.SIGNIFICANT_MOTION](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.SIGNIFICANT_MOTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **SignificantMotionResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-22"></a>

## on

```TypeScript
function on(type: SensorId.WEAR_DETECTION, callback: Callback<WearDetectionResponse>,
    options?: Options): void
```

Subscribes to data of the wear detection sensor.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.WEAR_DETECTION](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.WEAR_DETECTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **WearDetectionResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-23"></a>

## on

```TypeScript
function on(type: SensorId.FUSION_PRESSURE, callback: Callback<FusionPressureResponse>,
    options?: Options): void
```

Subscribes to the fused pressure sensor data.

**Since:** 22

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.FUSION_PRESSURE](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at SensorId.FUSION_PRESSURE. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FusionPressureResponse](arkts-sensorservice-sensor-fusionpressureresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **FusionPressureResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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


<a id="on-24"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback<AccelerometerResponse>,
    options?: Options): void
```

Subscribes to data changes of the acceleration sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-2)(type: SensorId.ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.ACCELEROMETER

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_ACCELEROMETER](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ACCELEROMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerResponse](arkts-sensorservice-sensor-accelerometerresponse-i.md)&gt; | Yes | Callback used to return the acceleration sensor data. The reported data type in the callback is **AccelerometerResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

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


<a id="on-25"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback: Callback<AccelerometerUncalibratedResponse>,
    options?: Options): void
```

Subscribes to data changes of the uncalibrated acceleration sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-3)(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback&lt;AccelerometerUncalibratedResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.ACCELEROMETER

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | Yes | Callback used to return the uncalibrated acceleration sensor data. The reported data type in the callback is **AccelerometerUncalibratedResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

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


<a id="on-26"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback<LightResponse>,
    options?: Options): void
```

Subscribes to data changes of the ambient light sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-4)(type: SensorId.AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_AMBIENT_LIGHT**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LightResponse](arkts-sensorservice-sensor-lightresponse-i.md)&gt; | Yes | Callback used to return the ambient light sensor data. The reported data type in the callback is **LightResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, (data: sensor.LightResponse) => {
  console.info('Succeeded in invoking on. Illumination: ' + data.intensity);
},
  { interval: 100000000 }
);
```


<a id="on-27"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback<AmbientTemperatureResponse>,
    options?: Options): void
```

Subscribes to data changes of the ambient temperature sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-5)(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback&lt;AmbientTemperatureResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_AMBIENT_TEMPERATURE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | Yes | Callback used to return the ambient temperature sensor data. The reported data type in the callback is **AmbientTemperatureResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, (data: sensor.AmbientTemperatureResponse) => {
  console.info('Succeeded in invoking on. Temperature: ' + data.temperature);
},
  { interval: 100000000 }
);
```


<a id="on-28"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback<BarometerResponse>,
    options?: Options): void
```

Subscribes to data changes of the barometer sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-6)(type: SensorId.BAROMETER, callback: Callback&lt;BarometerResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_BAROMETER](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_BAROMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BarometerResponse](arkts-sensorservice-sensor-barometerresponse-i.md)&gt; | Yes | Callback used to return the barometer sensor data. The reported data type in the callback is **BarometerResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_BAROMETER, (data: sensor.BarometerResponse) => {
  console.info('Succeeded in invoking on. Atmospheric pressure: ' + data.pressure);
},
  { interval: 100000000 }
);
```


<a id="on-29"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback<GravityResponse>,
    options?: Options): void
```

Subscribes to data changes of the gravity sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-7)(type: SensorId.GRAVITY, callback: Callback&lt;GravityResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_GRAVITY](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GRAVITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | Yes | Callback used to return the gravity sensor data. The reported data type in the callback is **GravityResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

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


<a id="on-30"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback<GyroscopeResponse>,
    options?: Options): void
```

Subscribes to data changes of the gyroscope sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-8)(type: SensorId.GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.GYROSCOPE

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_GYROSCOPE](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GYROSCOPE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeResponse](arkts-sensorservice-sensor-gyroscoperesponse-i.md)&gt; | Yes | Callback used to return the gyroscope sensor data. The reported data type in the callback is **GyroscopeResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

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


<a id="on-31"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback: Callback<GyroscopeUncalibratedResponse>,
    options?: Options): void
```

Subscribes to data changes of the uncalibrated gyroscope sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-9)(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback&lt;GyroscopeUncalibratedResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.GYROSCOPE

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md)&gt; | Yes | Callback used to return the uncalibrated gyroscope sensor data. The reported data type in the callback is **GyroscopeUncalibratedResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

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


<a id="on-32"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback<HallResponse>,
    options?: Options): void
```

Subscribes to data changes of the Hall effect sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-10)(type: SensorId.HALL, callback: Callback&lt;HallResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_HALL](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HALL**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | Yes | Callback used to return the Hall effect sensor data. The reported data type in the callback is **HallResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. The default value is 200,000,000 ns. This parameter is used to set the data reporting frequency when Hall effect events are frequently triggered. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_HALL, (data: sensor.HallResponse) => {
  console.info('Succeeded in invoking on. Status: ' + data.status);
},
  { interval: 100000000 }
);
```


<a id="on-33"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback<HeartRateResponse>,
    options?: Options): void
```

Subscribes to data changes of the heart rate sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-11)(type: SensorId.HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.HEALTH_DATA

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_HEART_RATE](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HEART_RATE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HeartRateResponse](arkts-sensorservice-sensor-heartrateresponse-i.md)&gt; | Yes | Callback used to return the heart rate sensor data. The reported data type in the callback is **HeartRateResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |


<a id="on-34"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback<HumidityResponse>,
    options?: Options): void
```

Subscribes to data changes of the humidity sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-12)(type: SensorId.HUMIDITY, callback: Callback&lt;HumidityResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_HUMIDITY](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HUMIDITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md)&gt; | Yes | Callback used to return the humidity sensor data. The reported data type in the callback is **HumidityResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_HUMIDITY, (data: sensor.HumidityResponse) => {
  console.info('Succeeded in invoking on. Humidity: ' + data.humidity);
},
  { interval: 100000000 }
);
```


<a id="on-35"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback: Callback<LinearAccelerometerResponse>,
    options?: Options): void
```

Subscribes to data changes of the linear acceleration sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-13)(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback&lt;LinearAccelerometerResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.ACCELEROMETER

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_LINEAR_ACCELERATION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | Yes | Callback used to return the linear acceleration sensor data. The reported data type in the callback is **LinearAccelerometerResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |


<a id="on-36"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback<MagneticFieldResponse>,
    options?: Options): void
```

Subscribes to data changes of the magnetic field sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-14)(type: SensorId.MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_MAGNETIC_FIELD**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | Yes | Callback used to return the magnetic field sensor data. The reported data type in the callback is **MagneticFieldResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

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


<a id="on-37"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback<MagneticFieldUncalibratedResponse>,
    options?: Options): void
```

Subscribes to data changes of the uncalibrated magnetic field sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-15)(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | Yes | Callback used to return the uncalibrated magnetic field sensor data. The reported data type in the callback is **MagneticFieldUncalibratedResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

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


<a id="on-38"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback<OrientationResponse>,
    options?: Options): void
```

Subscribes to data changes of the orientation sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-16)(type: SensorId.ORIENTATION, callback: Callback&lt;OrientationResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_ORIENTATION](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ORIENTATION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | Yes | Callback used to return the orientation sensor data. The reported data type in the callback is **OrientationResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

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


<a id="on-39"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback<PedometerResponse>,
    options?: Options): void
```

Subscribes to data changes of the pedometer sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-17)(type: SensorId.PEDOMETER, callback: Callback&lt;PedometerResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_PEDOMETER](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PEDOMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | Yes | Callback used to return the pedometer sensor data. The reported data type in the callback is **PedometerResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER, (data: sensor.PedometerResponse) => {
  console.info('Succeeded in invoking on. Steps: ' + data.steps);
},
  { interval: 100000000 }
);
```


<a id="on-40"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback: Callback<PedometerDetectionResponse>,
    options?: Options): void
```

Subscribes to data changes of the pedometer detection sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-18)(type: SensorId.PEDOMETER_DETECTION, callback: Callback&lt;PedometerDetectionResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PEDOMETER_DETECTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md)&gt; | Yes | Callback used to return the pedometer detection sensor data. The reported data type in the callback is **PedometerDetectionResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, (data: sensor.PedometerDetectionResponse) => {
  console.info('Succeeded in invoking on. Scalar data: ' + data.scalar);
},
  { interval: 100000000 }
);
```


<a id="on-41"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback<ProximityResponse>,
    options?: Options): void
```

Subscribes to data changes of the proximity sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-19)(type: SensorId.PROXIMITY, callback: Callback&lt;ProximityResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_PROXIMITY](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PROXIMITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProximityResponse](arkts-sensorservice-sensor-proximityresponse-i.md)&gt; | Yes | Callback used to return the proximity sensor data. The reported data type in the callback is **ProximityResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. The default value is 200,000,000 ns. This parameter is used to set the data reporting frequency when proximity sensor events are frequently triggered. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_PROXIMITY, (data: sensor.ProximityResponse) => {
  console.info('Succeeded in invoking on. Distance: ' + data.distance);
},
  { interval: 100000000 }
);
```


<a id="on-42"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback<RotationVectorResponse>,
    options?: Options): void
```

Subscribes to data changes of the rotation vector sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-20)(type: SensorId.ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ROTATION_VECTOR**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | Yes | Callback used to return the rotation vector sensor data. The reported data type in the callback is **RotationVectorResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

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


<a id="on-43"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback<SignificantMotionResponse>,
    options?: Options): void
```

Subscribes to data changes of the significant motion sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-21)(type: SensorId.SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_SIGNIFICANT_MOTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | Yes | Callback used to return the significant motion sensor data. The reported data type in the callback is **SignificantMotionResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

sensor.on(sensor.SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, (data: sensor.SignificantMotionResponse) => {
  console.info('Succeeded in invoking on. Scalar data: ' + data.scalar);
},
  { interval: 100000000 }
);
```


<a id="on-44"></a>

## on

```TypeScript
function on(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback<WearDetectionResponse>,
    options?: Options): void
```

Subscribes to data changes of the wear detection sensor. If this API is called multiple times for the same application, the last call takes effect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](#on-22)(type: SensorId.WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;, options?: Options)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_WEAR_DETECTION](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_WEAR_DETECTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | Yes | Callback used to return the wear detection sensor data. The reported data type in the callback is **WearDetectionResponse**. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | List of optional parameters. This parameter is used to set the data reporting frequency. The default value is 200,000,000 ns. |

**Examples**

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

Enables listening for sensor status changes. This API asynchronously returns the result through a callback.

**Since:** 19

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sensorStatusChange' | Yes | Event type. The value **sensorStatusChange** indicates the sensor status change event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SensorStatusEvent](arkts-sensorservice-sensor-sensorstatusevent-i.md)&gt; | Yes | Callback used to return the sensor status change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
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
