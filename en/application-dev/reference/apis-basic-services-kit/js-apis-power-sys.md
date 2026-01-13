# @ohos.power (Power Management) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @w_Machine_cc-->

The **power** module provides APIs for rebooting and shutting down the system, as well as querying the screen status.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.power (Power Management)](js-apis-power.md).

## Modules to Import

```js
import {power} from '@kit.BasicServicesKit';
```

## power.shutdown

shutdown(reason: string): void

Shuts down the system.

**System API**: This is a system API.

**Required permission**: ohos.permission.REBOOT

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| reason | string | Yes   | Shutdown reason. The value must be a string.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |


**Example**

```js
try {
    power.shutdown('shutdown_test');
} catch(err) {
    console.error('shutdown failed, err: ' + err);
}
```

## power.reboot<sup>9+</sup>

reboot(reason: string): void

Reboots a device.

**System API**: This is a system API.

**Required permission**: ohos.permission.REBOOT

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| reason | string | Yes  | Reboot reason. The value must be a string.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
try {
    power.reboot('reboot_test');
} catch(err) {
    console.error('reboot failed, err: ' + err);
}
```

## power.wakeup<sup>9+</sup>

wakeup(detail: string): void

Wakes up a device.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_MANAGER

For API version 9 to 18, no permission is required; since API version 19, this permission is required.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| detail | string | Yes  | Wakeup reason. The value must be a string.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
try {
    power.wakeup('wakeup_test');
} catch(err) {
    console.error('wakeup failed, err: ' + err);
}
```

## power.suspend<sup>9+</sup>

suspend(isImmediate?: boolean): void

Enables a device to enter the sleep state.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_MANAGER

For API version 9 to 18, no permission is required; since API version 19, this permission is required.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| isImmediate<sup>10+</sup> | boolean |  No | Whether the device enters the sleep state immediately. The value **true** indicates that the device enters the sleep state immediately after the screen is turned off; **false** indicates that the system controls when the device enters the sleep state. If this parameter is not set, the default value **false** is used. If you only want to turn off the screen, you are advised not to set this parameter.<br>**NOTE**: This parameter is supported since API version 10.|


**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |

**Example**

```js
try {
    power.suspend();
} catch(err) {
    console.error('suspend failed, err: ' + err);
}
```

## power.setPowerMode<sup>9+</sup>

setPowerMode(mode: DevicePowerMode, callback: AsyncCallback&lt;void&gt;): void

Sets the power mode of a device. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.POWER_OPTIMIZATION

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name  | Type                                | Mandatory| Description                                                        |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| mode     | DevicePowerMode | Yes  | Power mode. The value must be an enum.                                                  |
| callback | AsyncCallback&lt;void&gt;            | Yes  | Callback invoked to return the result.<br>If the power mode is successfully set, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900301 | Setting the power mode failed. |
| 401     | Parameter error. Possible causes: 1.Parameter verification failed. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE, (err: Error) => {
    if (typeof err === 'undefined') {
        console.info('set power mode to MODE_PERFORMANCE');
    } else {
        console.error('set power mode failed, err: ' + err);
    }
});
```

## power.setPowerMode<sup>9+</sup>

setPowerMode(mode: DevicePowerMode): Promise&lt;void&gt;

Sets the power mode of a device. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.POWER_OPTIMIZATION

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name| Type                                | Mandatory| Description      |
| ------ | ------------------------------------ | ---- | ---------- |
| mode   | DevicePowerMode | Yes  | Power mode. The value must be an enum.|

**Return value**

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900301 | Setting the power mode failed. |
| 401     | Parameter error. Possible causes: 1.Parameter verification failed. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE)
.then(() => {
    console.info('set power mode to MODE_PERFORMANCE');
})
.catch((err : Error)=> {
    console.error('set power mode failed, err: ' + err);
});
```

## power.setScreenOffTime<sup>12+</sup>

setScreenOffTime(timeout: number): void

Sets the screen-off timeout duration.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_MANAGER

For API version 12 to 18, no permission is required; since API version 19, this permission is required.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| timeout | number | Yes   | Screen-off timeout duration, in milliseconds. A value greater than **0** indicates the specified timeout duration is used, and the value **-1** indicates that the default timeout duration is used. Other values are invalid.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1. Parameter verification failed. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
try {
    power.setScreenOffTime(30000);
} catch(err) {
    console.error('set screen off time failed, err: ' + err);
}
```

## power.hibernate<sup>12+</sup>

hibernate(clearMemory: boolean): void

Hibernates a device.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_MANAGER

For API version 12 to 18, no permission is required; since API version 19, this permission is required.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| clearMemory | boolean | Yes   | Whether to clear the memory. The value **true** means to clear the memory before the system enters the hibernation state, and the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |

**Example**

```js
try {
    power.hibernate(true);
} catch(err) {
    console.error('hibernate failed, err: ' + err);
}
```

## power.refreshActivity<sup>20+</sup>

refreshActivity(reason: string): void

Refreshes the device activity status (for example, resetting the screen-off time).
This API takes effect only when the device is active. For details about the device activity status, see [power.isActive](js-apis-power.md#powerisactive9).

**System API**: This is a system API.

**Required permissions**: ohos.permission.REFRESH_USER_ACTION

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| reason | string | Yes   | Reason for refreshing the device activity status. The value must be a string.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 4900201 |The device activity is being refreshed too frequently; the minimum time interval is 100 ms. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
try {
    power.refreshActivity('refreshActivity_test');
} catch(err) {
    console.error('refreshActivity failed, err: ' + err);
}
```

## power.setPowerKeyFilteringStrategy<sup>21+</sup>

setPowerKeyFilteringStrategy(strategy: PowerKeyFilteringStrategy): void;

Sets the power key filtering strategy. After the power service subscribes to the power key event, this API is used to configure the processing mode of this event.
For details about the power key filtering strategy, see [power.PowerKeyFilteringStrategy](js-apis-power.md#powerkeyfilteringstrategy21).

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_MANAGER

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| strategy | PowerKeyFilteringStrategy | Yes   | Power key filtering strategy. The value must be of the enum type.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
try {
    power.setPowerKeyFilteringStrategy(power.PowerKeyFilteringStrategy.LONG_PRESS_FILTERING_ONCE);
} catch(err) {
    console.error('setPowerKeyFilteringStrategy failed, err: ' + err);
}
```

## power.registerShutdownCallback<sup>23+</sup>

registerShutdownCallback(callback: Callback&lt;boolean&gt;): void

Registers a callback to be invoked when the device is shut down or rebooted. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.REBOOT

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name  | Type                        | Mandatory| Description                          |
| -------- | ---------------------------- | ---- | ------------------------------ |
| callback | Callback&lt;boolean&gt; | Yes  | Callback used to return the result. The value **true** indicates that the device is rebooted, and **false** indicates that the device is shut down.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
try {
    power.registerShutdownCallback((isReboot: boolean) => {
        console.info('device shutdown is: ' + isReboot);
    });
    console.info('register shutdown callback success.');
} catch(err) {
    console.error('register shutdown callback failed, err: ' + err);
}
```

## power.unregisterShutdownCallback<sup>23+</sup>

unregisterShutdownCallback(callback?: Callback\<void>): void

Unregisters the callback to be invoked when the device is shut down or rebooted. This API uses a callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.REBOOT

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                          |
| -------- | -------------------- | ---- | ---------------------------------------------- |
| callback | Callback&lt;void&gt; | No  | Callback that returns no value.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
try {
    power.unregisterShutdownCallback(() => {
        console.info('unsubscribe shutdown success.');
    });
    console.info('unregister shutdown callback success.');
} catch(err) {
    console.error('unregister shutdown callback failed, err: ' + err);
}
```
