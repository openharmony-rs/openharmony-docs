# once

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## once

```TypeScript
function once(type: SensorId.ACCELEROMETER, callback: Callback<AccelerometerResponse>): void
```

Obtains data of the acceleration sensor once.

**Since:** 9

**Required permissions:** ohos.permission.ACCELEROMETER

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.ACCELEROMETER](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.ACCELEROMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerResponse](arkts-sensorservice-sensor-accelerometerresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is an **AccelerometerResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback<AccelerometerUncalibratedResponse>): void
```

Obtains data of the uncalibrated acceleration sensor once.

**Since:** 9

**Required permissions:** ohos.permission.ACCELEROMETER

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.ACCELEROMETER_UNCALIBRATED](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.ACCELEROMETER_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is an **AccelerometerUncalibratedResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.AMBIENT_LIGHT, callback: Callback<LightResponse>): void
```

Obtains data of the ambient light sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.AMBIENT_LIGHT](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.AMBIENT_LIGHT**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LightResponse](arkts-sensorservice-sensor-lightresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **LightResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback<AmbientTemperatureResponse>): void
```

Obtains data of the temperature sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.AMBIENT_TEMPERATURE](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.AMBIENT_TEMPERATURE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is an **AmbientTemperatureResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.BAROMETER, callback: Callback<BarometerResponse>): void
```

Obtains data of the barometer sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.BAROMETER](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.BAROMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BarometerResponse](arkts-sensorservice-sensor-barometerresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **BarometerResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.GRAVITY, callback: Callback<GravityResponse>): void
```

Obtains data of the gravity sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.GRAVITY](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.GRAVITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **GravityResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.GYROSCOPE, callback: Callback<GyroscopeResponse>): void
```

Obtains data of the gyroscope sensor once.

**Since:** 9

**Required permissions:** ohos.permission.GYROSCOPE

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.GYROSCOPE](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.GYROSCOPE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeResponse](arkts-sensorservice-sensor-gyroscoperesponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **GyroscopeResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback<GyroscopeUncalibratedResponse>): void
```

Obtains data of the uncalibrated gyroscope sensor once.

**Since:** 9

**Required permissions:** ohos.permission.GYROSCOPE

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.GYROSCOPE_UNCALIBRATED](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.GYROSCOPE_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **GyroscopeUncalibratedResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.HALL, callback: Callback<HallResponse>): void
```

Obtains data of the Hall effect sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.HALL](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.HALL**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **HallResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.HEART_RATE, callback: Callback<HeartRateResponse>): void
```

Obtains data of the heart rate sensor once.

**Since:** 9

**Required permissions:** ohos.permission.READ_HEALTH_DATA

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.HEART_RATE](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.HEART_RATE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HeartRateResponse](arkts-sensorservice-sensor-heartrateresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **HeartRateResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.HUMIDITY, callback: Callback<HumidityResponse>): void
```

Obtains data of the humidity sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.HUMIDITY](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.HUMIDITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **HumidityResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback<LinearAccelerometerResponse>): void
```

Obtains data of the linear acceleration sensor once.

**Since:** 9

**Required permissions:** ohos.permission.ACCELEROMETER

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.LINEAR_ACCELEROMETER](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.LINEAR_ACCELEROMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **LinearAccelerometerResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.MAGNETIC_FIELD, callback: Callback<MagneticFieldResponse>): void
```

Obtains data of the magnetic field sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.MAGNETIC_FIELD](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **MagneticFieldResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback<MagneticFieldUncalibratedResponse>): void
```

Obtains data of the uncalibrated magnetic field sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.MAGNETIC_FIELD_UNCALIBRATED](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.MAGNETIC_FIELD_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **MagneticFieldUncalibratedResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.ORIENTATION, callback: Callback<OrientationResponse>): void
```

Obtains data of the orientation sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.ORIENTATION](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.ORIENTATION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **OrientationResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.PEDOMETER, callback: Callback<PedometerResponse>): void
```

Obtains data of the pedometer sensor once. The step counter sensor's data reporting is subject to some delay, and the delay is determined by specific product implementations.

**Since:** 9

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.PEDOMETER](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.PEDOMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **PedometerResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.PEDOMETER_DETECTION, callback: Callback<PedometerDetectionResponse>): void
```

Obtains data of the pedometer sensor once.

**Since:** 9

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.PEDOMETER_DETECTION](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.PEDOMETER_DETECTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **PedometerDetectionResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.PROXIMITY, callback: Callback<ProximityResponse>): void
```

Obtains data of the proximity sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.PROXIMITY](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.PROXIMITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProximityResponse](arkts-sensorservice-sensor-proximityresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **ProximityResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.ROTATION_VECTOR, callback: Callback<RotationVectorResponse>): void
```

Obtains data of the rotation vector sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.ROTATION_VECTOR](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.ROTATION_VECTOR**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **RotationVectorResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.SIGNIFICANT_MOTION, callback: Callback<SignificantMotionResponse>): void
```

Obtains the significant motion sensor data once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.SIGNIFICANT_MOTION](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.SIGNIFICANT_MOTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **SignificantMotionResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorId.WEAR_DETECTION, callback: Callback<WearDetectionResponse>): void
```

Obtains data of the wear detection sensor once.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.WEAR_DETECTION](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. The value is fixed at **SensorId.WEAR_DETECTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | Yes | Callback used to report the sensor data, which is a **WearDetectionResponse** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback<AccelerometerResponse>): void
```

Subscribes to only one data change of the acceleration sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](arkts-sensorservice-sensor-once-f.md)(type: SensorId.ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;)

**Required permissions:** ohos.permission.ACCELEROMETER

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_ACCELEROMETER](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ACCELEROMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerResponse](arkts-sensorservice-sensor-accelerometerresponse-i.md)&gt; | Yes | One-shot callback used to return the acceleration sensor data. The reported data type in the callback is **AccelerometerResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback: Callback<AccelerometerUncalibratedResponse>): void
```

Subscribes to only one data change of the uncalibrated acceleration sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-1)(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback: Callback&lt;AccelerometerUncalibratedResponse&gt;)

**Required permissions:** ohos.permission.ACCELEROMETER

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | Yes | One-shot callback used to return the uncalibrated acceleration sensor data. The reported data type in the callback is **AccelerometerUncalibratedResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback: Callback<LightResponse>): void
```

Subscribes to only one data change of the ambient light sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-2)(type: SensorId.AMBIENT_LIGHT, callback: Callback&lt;LightResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_AMBIENT_LIGHT**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LightResponse](arkts-sensorservice-sensor-lightresponse-i.md)&gt; | Yes | One-shot callback used to return the ambient light sensor data. The reported data type in the callback is **LightResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback: Callback<AmbientTemperatureResponse>): void
```

Subscribes to only one data change of the ambient temperature sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-3)(type: SensorId.AMBIENT_TEMPERATURE, callback: Callback&lt;AmbientTemperatureResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_AMBIENT_TEMPERATURE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | Yes | One-shot callback used to return the ambient temperature sensor data. The reported data type in the callback is **AmbientTemperatureResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback<BarometerResponse>): void
```

Subscribes to only one data change of the barometer sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-4)(type: SensorId.BAROMETER, callback: Callback&lt;BarometerResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_BAROMETER](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_BAROMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BarometerResponse](arkts-sensorservice-sensor-barometerresponse-i.md)&gt; | Yes | One-shot callback used to return the barometer sensor data. The reported data type in the callback is **BarometerResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback: Callback<GravityResponse>): void
```

Subscribes to only one data change of the gravity sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-5)(type: SensorId.GRAVITY, callback: Callback&lt;GravityResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_GRAVITY](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GRAVITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | Yes | One-shot callback used to return the gravity sensor data. The reported data type in the callback is **GravityResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback<GyroscopeResponse>): void
```

Subscribes to only one data change of the gyroscope sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-6)(type: SensorId.GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;)

**Required permissions:** ohos.permission.GYROSCOPE

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_GYROSCOPE](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GYROSCOPE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeResponse](arkts-sensorservice-sensor-gyroscoperesponse-i.md)&gt; | Yes | One-shot callback used to return the gyroscope sensor data. The reported data type in the callback is **GyroscopeResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback: Callback<GyroscopeUncalibratedResponse>): void
```

Subscribes to only one data change of the uncalibrated gyroscope sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-7)(type: SensorId.GYROSCOPE_UNCALIBRATED, callback: Callback&lt;GyroscopeUncalibratedResponse&gt;)

**Required permissions:** ohos.permission.GYROSCOPE

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md)&gt; | Yes | One-shot callback used to return the uncalibrated gyroscope sensor data. The reported data type in the callback is **GyroscopeUncalibratedResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_HALL, callback: Callback<HallResponse>): void
```

Subscribes to only one data change of the Hall effect sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-8)(type: SensorId.HALL, callback: Callback&lt;HallResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_HALL](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HALL**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | Yes | One-shot callback used to return the Hall effect sensor data. The reported data type in the callback is **HallResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback<HeartRateResponse>): void
```

Subscribes to only one data change of the heart rate sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-9)(type: SensorId.HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;)

**Required permissions:** ohos.permission.HEART_RATE

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_HEART_RATE](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HEART_RATE**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HeartRateResponse](arkts-sensorservice-sensor-heartrateresponse-i.md)&gt; | Yes | One-shot callback used to return the heart rate sensor data. The reported data type in the callback is **HeartRateResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback: Callback<HumidityResponse>): void
```

Subscribes to only one data change of the humidity sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-10)(type: SensorId.HUMIDITY, callback: Callback&lt;HumidityResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_HUMIDITY](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_HUMIDITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md)&gt; | Yes | One-shot callback used to return the humidity sensor data. The reported data type in the callback is **HumidityResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback: Callback<LinearAccelerometerResponse>): void
```

Subscribes to only one data change of the linear acceleration sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-11)(type: SensorId.LINEAR_ACCELEROMETER, callback: Callback&lt;LinearAccelerometerResponse&gt;)

**Required permissions:** ohos.permission.ACCELEROMETER

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_LINEAR_ACCELERATION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | Yes | One-shot callback used to return the linear acceleration sensor data. The reported data type in the callback is **LinearAccelerometerResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback: Callback<MagneticFieldResponse>): void
```

Subscribes to only one data change of the magnetic field sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-12)(type: SensorId.MAGNETIC_FIELD, callback: Callback&lt;MagneticFieldResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_MAGNETIC_FIELD**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | Yes | One-shot callback used to return the magnetic field sensor data. The reported data type in the callback is **MagneticFieldResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback: Callback<MagneticFieldUncalibratedResponse>): void
```

Subscribes to only one data change of the uncalibrated magnetic field sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-13)(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback: Callback&lt;MagneticFieldUncalibratedResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | Yes | One-shot callback used to return the uncalibrated magnetic field sensor data. The reported data type in the callback is **MagneticFieldUncalibratedResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback<OrientationResponse>): void
```

Subscribes to only one data change of the orientation sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-14)(type: SensorId.ORIENTATION, callback: Callback&lt;OrientationResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_ORIENTATION](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ORIENTATION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | Yes | One-shot callback used to return the orientation sensor data. The reported data type in the callback is **OrientationResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback<PedometerResponse>): void
```

Subscribes to only one data change of the pedometer sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-15)(type: SensorId.PEDOMETER, callback: Callback&lt;PedometerResponse&gt;)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_PEDOMETER](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PEDOMETER**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | Yes | One-shot callback used to return the pedometer sensor data. The reported data type in the callback is **PedometerResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback: Callback<PedometerDetectionResponse>): void
```

Subscribes to only one data change of the pedometer detection sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-16)(type: SensorId.PEDOMETER_DETECTION, callback: Callback&lt;PedometerDetectionResponse&gt;)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PEDOMETER_DETECTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md)&gt; | Yes | One-shot callback used to return the pedometer detection sensor data. The reported data type in the callback is **PedometerDetectionResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback: Callback<ProximityResponse>): void
```

Subscribes to only one data change of the proximity sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-17)(type: SensorId.PROXIMITY, callback: Callback&lt;ProximityResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_PROXIMITY](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_PROXIMITY**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProximityResponse](arkts-sensorservice-sensor-proximityresponse-i.md)&gt; | Yes | One-shot callback used to return the proximity sensor data. The reported data type in the callback is **ProximityResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback: Callback<RotationVectorResponse>): void
```

Subscribes to only one data change of the rotation vector sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-18)(type: SensorId.ROTATION_VECTOR, callback: Callback&lt;RotationVectorResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_ROTATION_VECTOR**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | Yes | One-shot callback used to return the rotation vector sensor data. The reported data type in the callback is **RotationVectorResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback: Callback<SignificantMotionResponse>): void
```

Subscribes to only one data change of the significant motion sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-19)(type: SensorId.SIGNIFICANT_MOTION, callback: Callback&lt;SignificantMotionResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_SIGNIFICANT_MOTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | Yes | One-shot callback used to return the significant motion sensor data. The reported data type in the callback is **SignificantMotionResponse**. |


## once

```TypeScript
function once(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback<WearDetectionResponse>): void
```

Subscribes to only one data change of the wear detection sensor.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [once](#once-20)(type: SensorId.WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorType.SENSOR_TYPE_ID_WEAR_DETECTION](arkts-sensorservice-sensor-sensortype-e.md) | Yes | Type of the sensor to subscribe to, which is **SENSOR_TYPE_ID_WEAR_DETECTION**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | Yes | One-shot callback used to return the wear detection sensor data. The reported data type in the callback is **WearDetectionResponse**. |
