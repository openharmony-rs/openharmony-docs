# @ohos.sensor (Sensor) (System API)
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @LiuChao-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->

The **@system.sensor** module is a sensor data subscription module for lite wearables. It provides the data subscription and subscription cancellation capabilities for the acceleration, compass, distance, ambient light, pedometer, barometric pressure, heart rate, device wearing status, device orientation, and gyroscope sensors.

This module helps apps obtain sensor data change notifications in real time to implement functions such as fitness monitoring, health tracking, environment sensing, direction identification, and screen adaptation. Each sensor provides subscription and unsubscription APIs. The wearing status sensor additionally provides the **getOnBodyState** API for a single query.

For devices other than lightweight wearables, this module is no longer maintained since API version 8. You are advised to use the [@ohos.sensor](js-apis-sensor.md) module instead. If an app calls the subscription API for the same sensor multiple times, only the last call takes effect.

This module uses the subscription-unsubscription mode. You can call **sensor.on** to subscribe to sensor data, and the system will report the data at the specified interval. When the subscription is no longer needed, you can call **sensor.off** to cancel the subscription. **on** and **off** must be used in pairs. Subscription must be performed before unsubscription. If an app subscribes to the same sensor multiple times, only the last subscription takes effect. Since API version 19, the **sensorInfoParam** parameter has been added to **sensor.off**. This parameter allows you to cancel the sensor callback on a specified device based on **deviceId** and **sensorIndex**. If this parameter is not passed, the callback of the local device is canceled by default. In API version 10, **sensor.off** does not contain this parameter and can only cancel the callback of the local device.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { sensor } from '@kit.SensorServiceKit';
```

## sensor.on(sensor.SensorId.COLOR)<sup>10+</sup>

on(type: SensorId.COLOR, callback: Callback&lt;ColorResponse&gt;, options?: Options): void

Subscribes to data changes of the color sensor. This API uses an asynchronous callback to return the result. The color sensor data is reported asynchronously through a callback. The data is reported through a **ColorResponse** object, which contains two number fields: **lightIntensity** and **colorTemperature**.

This API is used when you need to obtain the ambient light intensity and color temperature to implement functions such as automatic screen brightness adjustment, color temperature compensation for photographing, and ambient light line monitoring.

**System capability**: SystemCapability.Sensors.Sensor

**System API**: This is a system API.

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                       |
| -------- | ------------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).COLOR                      | Yes  | Sensor type. The value is fixed at **SensorId.COLOR**.                     |
| callback | Callback&lt;[ColorResponse](#colorresponse10)&gt; | Yes  | Callback used to report the sensor data, which is a **ColorResponse** object.        |
| options  | [Options](js-apis-sensor.md#options)              | No  | Optional parameters used to set the reporting frequency of the sensor, in nanoseconds. The default value is **200000000**. If this parameter is not passed, the default frequency is used.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission check failed. A non-system application uses the system API. <br>Applicable versions: 11+|
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
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

## sensor.on(sensor.SensorId.SAR)<sup>10+</sup>

on(type: SensorId.SAR, callback: Callback&lt;SarResponse&gt;, options?: Options): void

Subscribes to data changes of the Sodium Adsorption Ratio (SAR) sensor. This API uses an asynchronous callback to return the result. The SAR sensor data is reported asynchronously through a callback. The data is reported through a **SarResponse** object, which contains one number field: **absorptionRatio**.

This API can be used to monitor the SAR of a device to implement functions such as communication security detection and radiation detection.

**System capability**: SystemCapability.Sensors.Sensor

**System API**: This is a system API.

**Parameters**

| Name  | Type                                         | Mandatory| Description                                                       |
| -------- | --------------------------------------------- | ---- | ----------------------------------------------------------- |
| type     | [SensorId](#sensorid9).SAR                    | Yes  | Sensor type. The value is fixed at **SensorId.SAR**.                       |
| callback | Callback&lt;[SarResponse](#sarresponse10)&gt; | Yes  | Callback used to report the sensor data, which is a **SarResponse** object.          |
| options  | [Options](js-apis-sensor.md#options)          | No  | Optional parameters used to set the reporting frequency of the sensor, in nanoseconds. The default value is **200000000**. If this parameter is not passed, the default frequency is used.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission check failed. A non-system application uses the system API. <br>Applicable versions: 11+|
| 401      | Parameter error.Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
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

## sensor.off(sensor.SensorId.COLOR)<sup>10+</sup>

off(type: SensorId.COLOR, callback?: Callback&lt;ColorResponse&gt;): void

Unsubscribes from data of the color sensor. After this method is called, the callback for the color sensor will not be triggered.

When the color sensor data is no longer needed (for example, when the page is switched or the app is exited), call this method to cancel the subscription to reduce system resource usage.

After this method is called, the callback registered using **sensor.on(sensor.SensorId.COLOR)** will not be triggered. If the **callback** parameter is passed, only the specified callback is unregistered. If the **callback** parameter is not passed, all callbacks of the **SensorId.COLOR** type are unregistered. You need to call **sensor.on(sensor.SensorId.COLOR)** to register to the callback before calling this method for unregistration.

**System capability**: SystemCapability.Sensors.Sensor

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                    | Mandatory| Description                                                        |
| -------- |--------------------------------------------------------| ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).COLOR                           | Yes  | Sensor type. The value is fixed at **SensorId.COLOR**.                      |
| callback | Callback&lt;[ColorResponse](#colorresponse10)&gt;      | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission check failed. A non-system application uses the system API. <br>Applicable versions: 11+|
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

## sensor.off(sensor.SensorId.COLOR)<sup>19+</sup>

off(type: SensorId.COLOR, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;ColorResponse&gt;): void

Unsubscribes from data of the color sensor. Compared with the **off** API in API version 10, the **sensorInfoParam** parameter is added to this API. You can use **deviceId** and **sensorIndex** to specify the callback of a specific sensor on a device. This API is applicable to multi-device scenarios.

Use this API when you need to unsubscribe from the color sensor data of a specific device (for example, in a multi-device connection scenario). If **sensorInfoParam** is not passed, the callback of the local device (whose **deviceId** is -1) is unregistered by default.

After this API is called, the callback function of the color sensor on the specified device will not be triggered. If the **callback** parameter is passed, only the specified callback is unregistered. If the **callback** parameter is not passed, all callbacks of the **SensorId.COLOR** type on the specified device are unregistered.

**System capability**: SystemCapability.Sensors.Sensor

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                    | Mandatory| Description                                                        |
| -------- |--------------------------------------------------------| ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).COLOR                           | Yes  | Sensor type. The value is fixed at **SensorId.COLOR**.                      |
| sensorInfoParam | [SensorInfoParam](js-apis-sensor.md#sensorinfoparam19) |  No| Sensor parameters, including **deviceId** and **sensorIndex**. The default value of **deviceId** is **-1**, indicating the local device. The default value of **sensorIndex** is **0**, indicating the default sensor. If this parameter is not passed, the callback on the local device is canceled by default.|
| callback | Callback&lt;[ColorResponse](#colorresponse10)&gt;      | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type on the specified device are unregistered.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission check failed. A non-system application uses the system API. |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
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

## sensor.off(sensor.SensorId.SAR)<sup>10+</sup>

off(type: SensorId.SAR, callback?: Callback&lt;SarResponse&gt;): void

Unsubscribes from data of the SAR sensor. After this method is called, the callback for the SAR sensor will not be triggered.

When the SAR sensor data is no longer needed (for example, when the page is switched or the app is exited), call this method to cancel the subscription to reduce system resource usage.

After this method is called, the callback registered using **sensor.on(sensor.SensorId.SAR)** will not be triggered. If the **callback** parameter is passed, only the specified callback is unregistered. If the **callback** parameter is not passed, all callbacks of the **SensorId.SAR** type are unregistered. You need to call **sensor.on(sensor.SensorId.SAR)** to register to the callback before calling this method for unregistration.

**System capability**: SystemCapability.Sensors.Sensor

**System API**: This is a system API.

**Parameters**

| Name  | Type                                         | Mandatory| Description                                                        |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).SAR                    | Yes  | Sensor type. The value is fixed at **SensorId.SAR**.                        |
| callback | Callback&lt;[SarResponse](#sarresponse10)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission check failed. A non-system application uses the system API. <br>Applicable versions: 11+|
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

## sensor.off(sensor.SensorId.SAR)<sup>19+</sup>

off(type: SensorId.SAR, sensorInfoParam?: SensorInfoParam, callback?: Callback&lt;SarResponse&gt;): void

Unsubscribes from data of the SAR sensor. Compared with the **off** API in API version 10, the **sensorInfoParam** parameter is added to this API. You can use **deviceId** and **sensorIndex** to specify the callback of a specific sensor on a device. This API is applicable to multi-device scenarios.

Use this API when you need to unsubscribe from the SAR sensor data of a specific device (for example, in a multi-device connection scenario). If **sensorInfoParam** is not passed, the callback of the local device (whose **deviceId** is -1) is unregistered by default.

After this API is called, the callback function of the SAR sensor on the specified device will not be triggered. If the **callback** parameter is passed, only the specified callback is unregistered. If the **callback** parameter is not passed, all callbacks of the **SensorId.SAR** type on the specified device are unregistered.

**System capability**: SystemCapability.Sensors.Sensor

**System API**: This is a system API.

**Parameters**

| Name  | Type                                         | Mandatory| Description                                                        |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [SensorId](#sensorid9).SAR                    | Yes  | Sensor type. The value is fixed at **SensorId.SAR**.                        |
| sensorInfoParam | [SensorInfoParam](js-apis-sensor.md#sensorinfoparam19) |  No| Sensor parameters, including **deviceId** and **sensorIndex**. The default value of **deviceId** is **-1**, indicating the local device. The default value of **sensorIndex** is **0**, indicating the default sensor. If this parameter is not passed, the callback on the local device is canceled by default.|
| callback | Callback&lt;[SarResponse](#sarresponse10)&gt; | No  | Callback to be unregistered. If this parameter is not specified, all callbacks of the specified sensor type on the specified device are unregistered.|

**Error codes**

For details about the error codes, see [Sensor Error Codes](errorcode-sensor.md) and [Universal Error Codes](../errorcode-universal.md). Error codes and error information are reported as exceptions. You need to use **try catch** to capture the exceptions that may occur during an API call.

| ID| Error Message                                                                                                                                   |
| -------- |-----------------------------------------------------------------------------------------------------------------------------------------|
| 202      | Permission check failed. A non-system application uses the system API.                                                                  |
| 14500101 | Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3.Sensor data channel exception. |

**Example**

```ts
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

## SensorId<sup>9+</sup>

Enumerates the sensor types.

**System capability**: SystemCapability.Sensors.Sensor

**System API**: This is a system API.

| Name               | Value  | Description                                           |
| ------------------- | ---- | ----------------------------------------------- |
| COLOR<sup>10+</sup> | 14   | Color sensor. Subscribes to or unsubscribes from the color sensor data. The reported data is a [ColorResponse](#colorresponse10) object, which contains the light intensity and color temperature information.    |
| SAR<sup>10+</sup>   | 15   | Sodium Adsorption Ratio (SAR) sensor. Subscribes to or unsubscribes from the SAR sensor data. The reported data is a [SarResponse](#sarresponse10) object, which contains the SAR information.|

## ColorResponse<sup>10+</sup>

Describes the color sensor data. It extends from [Response](js-apis-sensor.md#response). This method is used to represent the response data reported by the color sensor, including the light intensity and color temperature information.

**System capability**: SystemCapability.Sensors.Sensor

**System API**: This is a system API.


| Name            | Type  | Read-Only| Optional| Description                         |
| ---------------- | ------ | ---- | ---- | ----------------------------- |
| lightIntensity   | number | No  | No  | Light intensity, in lux. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor. The typical indoor ambient light intensity ranges from 300 lux to 500 lux, and the outdoor sunlight intensity can reach over 10,000 lux.|
| colorTemperature | number | No  | No  | Color temperature, in K (Kelvin). Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor. In general, the color temperature of warm white light is 2700 to 3000 K, of neutral white light is 4000–5000 K, and of cool white light is above 6500 K.    |

## SarResponse<sup>10+</sup>

Describes the SAR sensor data. It extends from [Response](js-apis-sensor.md#response). This method is used to represent the response data reported by the SAR sensor, including the SAR information.

**System capability**: SystemCapability.Sensors.Sensor

**System API**: This is a system API.


| Name           | Type  | Read-Only| Optional| Description                           |
| --------------- | ------ | ---- | ---- | ------------------------------- |
| absorptionRatio | number | No  | No  | Absorption ratio, in W/kg. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.|
