# on (System API)

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## on

```TypeScript
function on(type: SensorId.COLOR, callback: Callback<ColorResponse>, options?: Options): void
```

Subscribes to data changes of the color sensor. This API uses an asynchronous callback to return the result. The color sensor data is reported asynchronously through a callback. The data is reported through a **ColorResponse** object, which contains two number fields: **lightIntensity** and **colorTemperature**.

This API is used when you need to obtain the ambient light intensity and color temperature to implement functions such as automatic screen brightness adjustment, color temperature compensation for photographing, and ambient light line monitoring.

**Since:** 10

<!--Device-sensor-function on(type: SensorId.COLOR, callback: Callback<ColorResponse>, options?: Options): void--><!--Device-sensor-function on(type: SensorId.COLOR, callback: Callback<ColorResponse>, options?: Options): void-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.COLOR](arkts-sensorservice-sensor-sensorid-e-sys.md) | Yes | Sensor type. The value is fixed at **SensorId.COLOR**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ColorResponse](arkts-sensorservice-sensor-colorresponse-i-sys.md)&gt; | Yes | Callback used to report the sensor data, which is a **ColorResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | Optional parameters used to set the reporting frequency of the sensor, in nanoseconds. The default value is **200000000**. If this parameter is not passed, the default frequency is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br> Applicable versions: 11+ |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try{
  sensor.on(sensor.SensorId.COLOR, (data: sensor.ColorResponse) => {
    console.info('Succeeded in getting the intensity of light: ' + data.lightIntensity);
    console.info('Succeeded in getting the color temperature: ' + data.colorTemperature);
  }, { interval: 100000000 });
  setTimeout(() => {
        sensor.off(sensor.SensorId.COLOR);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```


<a id="on-1"></a>

## on

```TypeScript
function on(type: SensorId.SAR, callback: Callback<SarResponse>, options?: Options): void
```

Subscribes to data changes of the Sodium Adsorption Ratio (SAR) sensor. This API uses an asynchronous callback to return the result. The SAR sensor data is reported asynchronously through a callback. The data is reported through a **SarResponse** object, which contains one number field: **absorptionRatio**.

This API can be used to monitor the SAR of a device to implement functions such as communication security detection and radiation detection.

**Since:** 10

<!--Device-sensor-function on(type: SensorId.SAR, callback: Callback<SarResponse>, options?: Options): void--><!--Device-sensor-function on(type: SensorId.SAR, callback: Callback<SarResponse>, options?: Options): void-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.SAR](arkts-sensorservice-sensor-sensorid-e-sys.md) | Yes | Sensor type. The value is fixed at **SensorId.SAR**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SarResponse](arkts-sensorservice-sensor-sarresponse-i-sys.md)&gt; | Yes | Callback used to report the sensor data, which is a **SarResponse** object. |
| options | [Options](arkts-sensorservice-sensor-options-i.md) | No | Optional parameters used to set the reporting frequency of the sensor, in nanoseconds. The default value is **200000000**. If this parameter is not passed, the default frequency is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br> Applicable versions: 11+ |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  sensor.on(sensor.SensorId.SAR, (data: sensor.SarResponse) => {
    console.info('Succeeded in getting specific absorption rate : ' + data.absorptionRatio);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.SAR);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```
