# @ohos.thermal (Thermal Management)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=b026b3aeef31e5c2ac5c14f8507bb3fa0dee1101 translatedAt=2026-11-10T04:16:47.768Z pushedAt=2026-11-10T07:05:54.660Z nl=1 -->

The **thermal** module provides thermal level-related callback and query APIs to obtain the information required for thermal control.

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
 
- Only one callback can be resgistered for each process. If the callback is resgistered repeatedly, the previous one will be overwritten.
- The callback function should return a result as soon as possible and must not perform time-consuming operations such as synchronous file I/O. Otherwise, it may block the delivery of system thermal level notifications.
- After the thermal management service restarts abnormally, the registered callback automatically becomes invalid and no notification will be received. You need to call **registerThermalLevelCallback** again to restore the registration.
- When the thermal management service is unavailable, the registration may fail silently without throwing an exception. You cannot determine whether the registration succeeds from the return value. You are advised to verify service availability through [thermal.getLevel](#thermalgetlevel9) after registration. If [thermal.getLevel](#thermalgetlevel9) returns **COOL** while the device is obviously heating up, the service may be unavailable.

**System capability**: SystemCapability.PowerManager.ThermalManager

**Parameters**

| Name  | Type                        | Mandatory| Description                          |
| -------- | ---------------------------- | ---- | ------------------------------ |
| callback | Callback&lt;[ThermalLevel](#thermallevel)&gt; | Yes  | Callback used to return thermal level. This parameter is of the function type.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message   |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types. |

**Example**

```js
try {
    thermal.registerThermalLevelCallback((level: thermal.ThermalLevel) => {
        console.info('thermal level is: ' + level);
    });
    console.info('register thermal level callback success.');
} catch(err) {
    console.error('register thermal level callback failed, err: ' + err);
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

| Error Code  | Error Message   |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types. |

**Example**

```js
try {
    thermal.unregisterThermalLevelCallback(() => {
        console.info('unsubscribe thermal level success.');
    });
    console.info('unregister thermal level callback success.');
} catch(err) {
    console.error('unregister thermal level callback failed, err: ' + err);
}
```

## thermal.getLevel<sup>9+</sup>

getLevel(): ThermalLevel

Obtains the current thermal level.

**System capability**: SystemCapability.PowerManager.ThermalManager


**Return value**

| Type        | Description        |
| ------------ | ------------ |
| [ThermalLevel](#thermallevel) | Thermal level.|

**Example**

```js
let level = thermal.getLevel();
console.info('thermal level is: ' + level);
```

## thermal.subscribeThermalLevel<sup>(deprecated)</sup>

subscribeThermalLevel(callback: AsyncCallback&lt;ThermalLevel&gt;): void

Subscribes to thermal level changes. This API uses an asynchronous callback to return the result.

> **NOTE**<br>This API is supported since API version 8 and deprecated since API version 9. You are advised to use [thermal.registerThermalLevelCallback](#thermalregisterthermallevelcallback9) instead.

**System capability**: SystemCapability.PowerManager.ThermalManager

**Parameters**

| Name  | Type                             | Mandatory| Description                                                        |
| -------- | --------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;[ThermalLevel](#thermallevel)&gt; | Yes  | Callback used to return thermal level. This parameter is of the function type.|

**Example**

```js
thermal.subscribeThermalLevel((err: Error, level: thermal.ThermalLevel) => {
    console.info('thermal level is: ' + level);
});
```

## thermal.unsubscribeThermalLevel<sup>(deprecated)</sup>

unsubscribeThermalLevel(callback?: AsyncCallback\<void>): void

Unsubscribes from thermal level changes. This API uses an asynchronous callback to return the result.

> **NOTE**<br>This API is supported since API version 8 and deprecated since API version 9. You are advised to use [thermal.unregisterThermalLevelCallback](#thermalunregisterthermallevelcallback9) instead.

**System capability**: SystemCapability.PowerManager.ThermalManager

**Parameters**

| Name  | Type                     | Mandatory| Description                                          |
| -------- | ------------------------- | ---- | ---------------------------------------------- |
| callback | AsyncCallback&lt;void&gt; | No  | Callback that returns no value. If this parameter is not set, all callbacks will be unregistered.|

**Example**

```js
thermal.unsubscribeThermalLevel(() => {
    console.info('unsubscribe thermal level success.');
});
```

## thermal.getThermalLevel<sup>(deprecated)</sup>

getThermalLevel(): ThermalLevel

Obtains the current thermal level.

> **NOTE**<br>This API is supported since API version 8 and deprecated since API version 9. You are advised to use [thermal.getLevel](#thermalgetlevel9) instead.

**System capability**: SystemCapability.PowerManager.ThermalManager

**Return value**

| Type          | Description    |
| ------------ | ------ |
| [ThermalLevel](#thermallevel) | Thermal level.|

**Example**

```js
let level = thermal.getThermalLevel();
console.info('thermal level is: ' + level);
```

## ThermalLevel

Enumerates thermal levels.

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
| ESCAPE<sup>11+</sup>     | 7    | The device is about to enter the escape state. You need to stop all services and take necessary emergency measures such as data backup.<br>Note: This API is supported since API version 11.|