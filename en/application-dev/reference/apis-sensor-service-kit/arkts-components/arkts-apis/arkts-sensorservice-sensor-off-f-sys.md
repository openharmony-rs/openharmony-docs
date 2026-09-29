# off (System API)

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## off

```TypeScript
function off(type: SensorId.COLOR, callback?: Callback<ColorResponse>): void
```

Unsubscribes from data of the color sensor. After this method is called, the callback for the color sensor will not be triggered.

When the color sensor data is no longer needed (for example, when the page is switched or the app is exited), call this method to cancel the subscription to reduce system resource usage.

After this method is called, the callback registered using **sensor.on(sensor.SensorId.COLOR)** will not be triggered. If the **callback** parameter is passed, only the specified callback is unregistered. If the **callback** parameter is not passed, all callbacks of the **SensorId.COLOR** type are unregistered. You need to call **sensor.on(sensor.SensorId.COLOR)** to register to the callback before calling this method for unregistration.

**Since:** 10

<!--Device-sensor-function off(type: SensorId.COLOR, callback?: Callback<ColorResponse>): void--><!--Device-sensor-function off(type: SensorId.COLOR, callback?: Callback<ColorResponse>): void-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.COLOR](arkts-sensorservice-sensor-sensorid-e-sys.md) | Yes | Sensor type. The value is fixed at **SensorId.COLOR**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ColorResponse](arkts-sensorservice-sensor-colorresponse-i-sys.md)&gt; | No | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br> Applicable versions: 11+ |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

try {
  sensor.on(sensor.SensorId.COLOR, callback1);
  sensor.on(sensor.SensorId.COLOR, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.COLOR, callback1);
  // Unsubscribe from all callbacks of the SensorId.COLOR type.
  sensor.off(sensor.SensorId.COLOR);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


<a id="off-1"></a>

## off

```TypeScript
function off(type: SensorId.COLOR, sensorInfoParam?: SensorInfoParam, callback?: Callback<ColorResponse>): void
```

Unsubscribes from data of the color sensor. Compared with the **off** API in API version 10, the **sensorInfoParam** parameter is added to this API. You can use **deviceId** and **sensorIndex** to specify the callback of a specific sensor on a device. This API is applicable to multi-device scenarios.

Use this API when you need to unsubscribe from the color sensor data of a specific device (for example, in a multi-device connection scenario). If **sensorInfoParam** is not passed, the callback of the local device (whose **deviceId** is -1) is unregistered by default.

After this API is called, the callback function of the color sensor on the specified device will not be triggered. If the **callback** parameter is passed, only the specified callback is unregistered. If the **callback** parameter is not passed, all callbacks of the **SensorId.COLOR** type on the specified device are unregistered.

**Since:** 19

<!--Device-sensor-function off(type: SensorId.COLOR, sensorInfoParam?: SensorInfoParam, callback?: Callback<ColorResponse>): void--><!--Device-sensor-function off(type: SensorId.COLOR, sensorInfoParam?: SensorInfoParam, callback?: Callback<ColorResponse>): void-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.COLOR](arkts-sensorservice-sensor-sensorid-e-sys.md) | Yes | Sensor type. The value is fixed at **SensorId.COLOR**. |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | No | Sensor parameters, including **deviceId** and **sensorIndex**. The default value of **deviceId** is **-1**, indicating the local device. The default value of **sensorIndex** is **0**, indicating the default sensor. If this parameter is not passed, the callback on the local device is canceled by default. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ColorResponse](arkts-sensorservice-sensor-colorresponse-i-sys.md)&gt; | No | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type on the specified device are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.ColorResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.COLOR;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
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


<a id="off-2"></a>

## off

```TypeScript
function off(type: SensorId.SAR, callback?: Callback<SarResponse>): void
```

Unsubscribes from data of the SAR sensor. After this method is called, the callback for the SAR sensor will not be triggered.

When the SAR sensor data is no longer needed (for example, when the page is switched or the app is exited), call this method to cancel the subscription to reduce system resource usage.

After this method is called, the callback registered using **sensor.on(sensor.SensorId.SAR)** will not be triggered. If the **callback** parameter is passed, only the specified callback is unregistered. If the **callback** parameter is not passed, all callbacks of the **SensorId.SAR** type are unregistered. You need to call **sensor.on(sensor.SensorId.SAR)** to register to the callback before calling this method for unregistration.

**Since:** 10

<!--Device-sensor-function off(type: SensorId.SAR, callback?: Callback<SarResponse>): void--><!--Device-sensor-function off(type: SensorId.SAR, callback?: Callback<SarResponse>): void-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.SAR](arkts-sensorservice-sensor-sensorid-e-sys.md) | Yes | Sensor type. The value is fixed at **SensorId.SAR**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SarResponse](arkts-sensorservice-sensor-sarresponse-i-sys.md)&gt; | No | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br> Applicable versions: 11+ |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

try {
  sensor.on(sensor.SensorId.SAR, callback1);
  sensor.on(sensor.SensorId.SAR, callback2);
  // Unsubscribe from callback1.
  sensor.off(sensor.SensorId.SAR, callback1);
  // Unsubscribe from all callbacks of the SensorId.SAR type.
  sensor.off(sensor.SensorId.SAR);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


<a id="off-3"></a>

## off

```TypeScript
function off(type: SensorId.SAR, sensorInfoParam?: SensorInfoParam, callback?: Callback<SarResponse>): void
```

Unsubscribes from data of the SAR sensor. Compared with the **off** API in API version 10, the **sensorInfoParam** parameter is added to this API. You can use **deviceId** and **sensorIndex** to specify the callback of a specific sensor on a device. This API is applicable to multi-device scenarios.

Use this API when you need to unsubscribe from the SAR sensor data of a specific device (for example, in a multi-device connection scenario). If **sensorInfoParam** is not passed, the callback of the local device (whose **deviceId** is -1) is unregistered by default.

After this API is called, the callback function of the SAR sensor on the specified device will not be triggered. If the **callback** parameter is passed, only the specified callback is unregistered. If the **callback** parameter is not passed, all callbacks of the **SensorId.SAR** type on the specified device are unregistered.

**Since:** 19

<!--Device-sensor-function off(type: SensorId.SAR, sensorInfoParam?: SensorInfoParam, callback?: Callback<SarResponse>): void--><!--Device-sensor-function off(type: SensorId.SAR, sensorInfoParam?: SensorInfoParam, callback?: Callback<SarResponse>): void-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId.SAR](arkts-sensorservice-sensor-sensorid-e-sys.md) | Yes | Sensor type. The value is fixed at **SensorId.SAR**. |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | No | Sensor parameters, including **deviceId** and **sensorIndex**. The default value of **deviceId** is **-1**, indicating the local device. The default value of **sensorIndex** is **0**, indicating the default sensor. If this parameter is not passed, the callback on the local device is canceled by default. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SarResponse](arkts-sensorservice-sensor-sarresponse-i-sys.md)&gt; | No | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type on the specified device are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// Sensor callback
const sensorCallback = (response: sensor.SarResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// Sensor type
const sensorType = sensor.SensorId.SAR;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
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
