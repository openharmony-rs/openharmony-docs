# @ohos.thermal (Thermal Management)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=84d49555fb850c5347aabc4d30f4ecc5b056b55e translatedAt=2026-11-06T01:45:15.090Z pushedAt=2026-11-09T06:15:44.309Z nl=1 -->

This module provides APIs for thermal management, including thermal level query and callback registration. The system divides the thermal status into multiple levels based on device temperature thresholds. For details, see [ThermalLevel](#thermallevel). When the device temperature crosses a level threshold, a callback notification is triggered, and you can execute implement service degradation policies based on the level.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import {thermal} from '@kit.BasicServicesKit';
```

## thermal.registerThermalLevelCallback<sup>9+</sup>

registerThermalLevelCallback(callback: Callback&lt;ThermalLevel&gt;): void

Registers a callback for thermal level changes. When the device temperature crosses a level threshold and causes the thermal level to change, the system automatically triggers a callback notification and returns the thermal level after the change through the callback. This API uses an asynchronous callback to return the result. This method is used in pairs with [thermal.unregisterThermalLevelCallback](#thermalunregisterthermallevelcallback9) which is used to unregister the callback for thermal level changes.

- Only one callback can be registered for each process. If the callback is registered repeatedly, the previous one will be overwritten.
- The callback function should return a result as soon as possible and must not perform time-consuming operations such as synchronous file I/O. Otherwise, it may block the delivery of system thermal level notifications.
- After the thermal management service restarts abnormally, the registered callback automatically becomes invalid and no notification will be received. You need to call **registerThermalLevelCallback** again to restore the registration.
- When the thermal management service is unavailable, the registration may fail silently without throwing an exception. You cannot determine whether the registration succeeds from the return value. You are advised to verify service availability through [thermal.getLevel](#thermalgetlevel9) after registration. If [thermal.getLevel](#thermalgetlevel9) returns **COOL** while the device is obviously heating up, the service may be unavailable.

**System capability**: SystemCapability.PowerManager.ThermalManager

**Parameters**

| Name  | Type                        | Mandatory| Description                          |
| -------- | ---------------------------- | ---- | ------------------------------ |
| callback | Callback&lt;[ThermalLevel](#thermallevel)&gt; | Yes | Callback used to return the thermal level after the change. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```js
try {
    thermal.registerThermalLevelCallback((level: thermal.ThermalLevel) => {
        console.info('thermal level is: ' + level);
    });
    console.info('register thermal level callback success.');
} catch (err) {
    console.error(`Failed to register thermal level callback. Code: ${err.code}, message: ${err.message}`);
}
```

## thermal.unregisterThermalLevelCallback<sup>9+</sup>

unregisterThermalLevelCallback(callback?: Callback\<void>): void

Unregisters the callback notification for thermal level changes. This API uses an asynchronous callback to return the result. This method is used in pairs with [thermal.registerThermalLevelCallback](#thermalregisterthermallevelcallback9). Unregistering a callback that is not registered does not report an error and is treated as no operation.

**System capability**: SystemCapability.PowerManager.ThermalManager

**Parameters**

| Name  | Type                | Mandatory| Description                                          |
| -------- | -------------------- | ---- | ---------------------------------------------- |
| callback | Callback&lt;void&gt; | No | Callback invoked when unregistration is complete. It has no return value. This parameter is used only to receive the notification of unregistration completion. After the unregistration succeeds, this callback  is invoked. If this parameter is not passed, the unregistration still takes effect, but no callback notification is triggered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types. |

**Example**

```js
try {
    thermal.unregisterThermalLevelCallback(() => {
        console.info('unsubscribe thermal level success.');
    });
    console.info('unregister thermal level callback success.');
} catch (err) {
    console.error(`Failed to unregister thermal level callback. Code: ${err.code}, message: ${err.message}`);
}
```

## thermal.getLevel<sup>9+</sup>

getLevel(): ThermalLevel

Obtains the current thermal level. The system determines the current thermal level in real time based on the device temperature and returns the corresponding level, based on which you can implement corresponding service degradation policies.

**System capability**: SystemCapability.PowerManager.ThermalManager


**Return value**

| Type        | Description        |
| ------------ | ------------ |
| [ThermalLevel](#thermallevel) | Thermal level of the current device, which reflects the temperature status of the device and can be used to guide the thermal control policy adjustment of services. |

**Example**

```js
let level = thermal.getLevel();
console.info('thermal level is: ' + level);
```

## thermal.subscribeThermalLevel<sup>(deprecated)</sup>

subscribeThermalLevel(callback: AsyncCallback&lt;ThermalLevel&gt;): void

Registers a callback for thermal level changes. This API uses an asynchronous callback to return the result. This method must be used in pairs with [thermal.unsubscribeThermalLevel](#thermalunsubscribethermalleveldeprecated) which is used to unregister the callback when listening is no longer needed.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [thermal.registerThermalLevelCallback](#thermalregisterthermallevelcallback9) instead.

**System capability**: SystemCapability.PowerManager.ThermalManager

**Parameters**

| Name  | Type                             | Mandatory| Description                                                        |
| -------- | --------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;[ThermalLevel](#thermallevel)&gt; | Yes | Callback used to return the thermal level after the change. |

**Example**

```js
thermal.subscribeThermalLevel((err: Error, level: thermal.ThermalLevel) => {
    if (err) {
        console.error('subscribe thermal level failed, err: ' + err);
        return;
    }
    console.info('thermal level is: ' + level);
});
```

## thermal.unsubscribeThermalLevel<sup>(deprecated)</sup>

unsubscribeThermalLevel(callback?: AsyncCallback\<void>): void

Unregisters the callback for thermal level changes. This API uses an asynchronous callback to return the result. This method is used in pairs with [thermal.subscribeThermalLevel](#thermalsubscribethermalleveldeprecated).

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [thermal.unregisterThermalLevelCallback](#thermalunregisterthermallevelcallback9) instead.

**System capability**: SystemCapability.PowerManager.ThermalManager

**Parameters**

| Name  | Type                     | Mandatory| Description                                          |
| -------- | ------------------------- | ---- | ---------------------------------------------- |
| callback | AsyncCallback&lt;void&gt; | No | Callback used to perform resource reclamation operations after the thermal level change callback is unregistered. No value is returned. |

**Example**

```js
thermal.unsubscribeThermalLevel(() => {
    console.info('unsubscribe thermal level success.');
});
```

## thermal.getThermalLevel<sup>(deprecated)</sup>

getThermalLevel(): ThermalLevel

Obtains the current thermal level.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [thermal.getLevel](#thermalgetlevel9) instead.

**System capability**: SystemCapability.PowerManager.ThermalManager

**Return value**

| Type          | Description    |
| ------------ | ------ |
| [ThermalLevel](#thermallevel) | Thermal level of the current device, which reflects the temperature status of the device and can be used to guide the thermal control policy of services. |

**Example**

```js
let level = thermal.getThermalLevel();
console.info('thermal level is: ' + level);
```

## ThermalLevel

Enumerates thermal levels.

Thermal levels progress from **COOL** to **ESCAPE**. The device status and recommended service actions corresponding to each level are shown in the following table.

**System capability**: SystemCapability.PowerManager.ThermalManager

| Name      | Value  | Description                                                        |
| ---------- | ---- | ------------------------------------------------------------ |
| COOL       | 0    | The device is cool, and services are not restricted.            |
| NORMAL     | 1    | The device is in the normal temperature range but it is getting warm. You need to downgrade or reduce the load of imperceptible services.|
| WARM       | 2    | The device is warm. You need to stop or delay some imperceptible services.|
| HOT        | 3    | The device is heating up. You need to stop all imperceptible services and downgrade or reduce the load of non-critical services.|
| OVERHEATED | 4    | The device is overheated. You need to stop all imperceptible services and downgrade or reduce the load of major foreground services.|
| WARNING    | 5    | The device is overheated and is about to enter the emergency state. You need to stop all imperceptible services and downgrade major foreground services to the maximum extent.|
| EMERGENCY  | 6    | The device has entered the emergency state. You need to stop all services except those for fundamental use.|
| ESCAPE<sup>11+</sup>     | 7    | The device is about to enter the thermal escape state, in which all services will be forcibly stopped. Services must take escape measures, such as saving important data. <br>**Note:** This API is supported since API version 11.|
