# @ohos.power (Power Management) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=5aff2357dc56653b2222b40c616bb5d5d16a22ec translatedAt=2026-11-12T04:31:38.773Z pushedAt=2026-11-12T12:22:54.030Z nl=1 -->

This module provides system APIs for device power state management, including shutting down and restarting a device, waking up a device, putting a device to sleep or into hibernation, setting the power mode, setting the screen-off timeout, refreshing the device active state, configuring the power key filtering policy, subscribing to and unsubscribing from shutdown/restart callbacks, and querying and setting power configurations. It applies to scenarios where system apps need to manage and control the device power state, such as controlling device power-on/off, hibernation and wakeup, power saving mode switching, and screen timeout management by device management apps. This module can help you implement refined management and automated control of device power behavior.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by this module. For details about its public APIs, see [@ohos.power (System Power Management)](js-apis-power.md).

## Modules to Import

```js
import { power, BusinessError } from '@kit.BasicServicesKit';
```

## power.shutdown

shutdown(reason: string): void

Shuts down the system. The difference between the **shutdown** and **reboot** methods is as follows: **shutdown** completely powers off the device so that it no longer runs, while **reboot** automatically restarts the device after it is powered off.

**System API**: This is a system API.

**Required permissions**: ohos.permission.REBOOT

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| reason | string | Yes    | Shutdown reason. |

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
} catch (err) {
    console.error(`Failed to shutdown. Code: ${err.code}, message: ${err.message}`);
}
```

## power.reboot<sup>9+</sup>

reboot(reason: string): void

Reboots a device.

**System API**: This is a system API.

**Required permissions**: ohos.permission.REBOOT

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| reason | string | Yes | Reason for the reboot. For example, **updater** indicates that the device enters the update mode after the reboot. If an empty string is passed in, the system enters the normal mode after the reboot. |

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
} catch (err) {
    console.error(`Failed to reboot. Code: ${err.code}, message: ${err.message}`);
}
```

## power.wakeup<sup>9+</sup>

wakeup(detail: string): void

Wakes up a device and restores it from the sleep state to the active state.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_MANAGER

For API versions 9 to 18, no permission is required to use this API. Since API version 19, the **ohos.permission.POWER_MANAGER** permission is required.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Device behavior differences:** When this API is called on a car device, error code 801 is returned. On other devices, it is called normally.

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| detail | string | Yes | Wakeup reason. |

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |
| 201     | Permission verification failed. The application does not have the permission required to call the API.<br>Applicable versions: 19+ |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 801     | Capability not supported. This API cannot work in car devices. <br>Applicable versions: 26.0.1+|

**Example**

```js
try {
    power.wakeup('wakeup_test');
} catch (err) {
    console.error(`Failed to wakeup device. Code: ${err.code}, message: ${err.message}`);
}
```

## power.suspend<sup>9+</sup>

suspend(isImmediate?: boolean): void

Enables a device to enter the sleep state.

After this method is called, the device enters the sleep state. To restore the device to the active state, call [power.wakeup](#powerwakeup9) to wake up the device.

The difference between the **suspend** and **hibernate** methods is as follows: when **suspend** is called, the device enters a shallower low-power sleep state (the device enters sleep after the screen is turned off); when **hibernate** is called, the device enters a deeper hibernation state (the buffer can be optionally cleared before hibernation). Use **suspend** when the device needs to be restored to the active state quickly, and use **hibernate** when power needs to be saved to the greatest extent.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_MANAGER

For API versions 9 to 18, no permission is required to use this API. Since API version 19, the **ohos.permission.POWER_MANAGER** permission is required.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Device behavior differences:** When this API is called on a car device, error code 801 is returned. On other devices, it is called normally.

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| isImmediate<sup>10+</sup> | boolean |  No  | Whether to put the device into sleep state directly. The value **true** means the device enters sleep immediately after the screen is turned off. If this parameter is not set, the default value **false** is used, which means the system automatically detects when to enter sleep after the screen is turned off. If you only want to turn off the screen, you are advised not to set this parameter.<br>**Note:** This parameter is supported since API version 10.|


**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API.<br>Applicable versions: 19+|
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 401     | Parameter error. Possible causes: 1. Parameter verification failed. |
| 4900701 | Failed to suspend the device. Possible causes: 1. Not allowed to turn off the screen during the exam.<br>Applicable versions: 26.0.1+ |
| 801     | Capability not supported. This API cannot work in car devices.<br>Applicable versions: 26.0.1+ |

**Example**

```js
try {
    power.suspend();
} catch (err) {
    console.error(`Failed to suspend device. Code: ${err.code}, message: ${err.message}`);
}
```

## power.setPowerMode<sup>9+</sup>

setPowerMode(mode: DevicePowerMode, callback: AsyncCallback&lt;void&gt;): void

Sets the power mode of the current device. Different power modes affect the performance and power consumption policies of the device. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_OPTIMIZATION

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name  | Type                                | Mandatory| Description                                                        |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| mode     | [DevicePowerMode](js-apis-power.md#devicepowermode9) | Yes   | Power mode. For the meaning of each mode, see the [DevicePowerMode](js-apis-power.md#devicepowermode9) enum. |
| callback | AsyncCallback&lt;void&gt;            | Yes  | Callback invoked to return the result.<br> If the power mode is successfully set, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900301 | Setting the power mode failed.<br>Applicable versions: 23+ |
| 401     | Parameter error. Possible causes: 1.Parameter verification failed. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 203     | This function is prohibited by enterprise management policies. <br>**Applicable versions:** 26.1.0+ |

**Example**

```js
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE, (err: BusinessError) => {
    if (err) {
        console.error(`Failed to set power mode. Code: ${err.code}, message: ${err.message}`);
        return;
    }
    console.info('set power mode to MODE_PERFORMANCE');
});
```

## power.setPowerMode<sup>9+</sup>

setPowerMode(mode: DevicePowerMode): Promise&lt;void&gt;

Sets the power mode of the current device. The power mode affects the performance and power consumption policies of the device. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_OPTIMIZATION

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name| Type                                | Mandatory| Description      |
| ------ | ------------------------------------ | ---- | ---------- |
| mode   | [DevicePowerMode](js-apis-power.md#devicepowermode9) | Yes   | Power mode. For the meaning of each mode, see the [DevicePowerMode](js-apis-power.md#devicepowermode9) enum. |

**Return value**

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900301 | Setting the power mode failed.<br>Applicable versions: 23+ |
| 401     | Parameter error. Possible causes: 1.Parameter verification failed. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 203     | This function is prohibited by enterprise management policies. <br>**Applicable versions:** 26.1.0+ |

**Example**

```js
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE)
.then(() => {
    console.info('set power mode to MODE_PERFORMANCE');
})
.catch((err: BusinessError) => {
    console.error(`Failed to set power mode. Code: ${err.code}, message: ${err.message}`);
});
```

## power.setScreenOffTime<sup>12+</sup>

setScreenOffTime(timeout: number): void

Sets the screen-off timeout duration. For example, a longer timeout duration can be set to keep the screen always on for self-service terminals or display devices, and a shorter timeout duration can be set to save power in low-battery scenarios.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_MANAGER

For API versions 12 to 18, no permission is required to use this API. Starting from API version 19, the **ohos.permission.POWER_MANAGER** permission is required.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Device behavior differences:** When this API is called on a car device, error code 801 is returned. On other devices, it is called normally.

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| timeout | number | Yes | Screen-off timeout duration, in milliseconds. A value greater than 0 indicates the screen-off timeout duration, and **-1** indicates restoring the default timeout duration. If any other value is passed, an exception is thrown with error code 401. |

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1. Parameter verification failed. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. <br>Applicable versions: 19+|
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 801     | Capability not supported. This API cannot work in car devices.<br>Applicable versions: 26.0.1+|

**Example**

```js
try {
    power.setScreenOffTime(30000);
} catch (err) {
    console.error(`Failed to set screen off time. Code: ${err.code}, message: ${err.message}`);
}
```

## power.hibernate<sup>12+</sup>

hibernate(clearMemory: boolean): void

Hibernates a device.

The difference between the **hibernate** and **suspend** methods is as follows: when **hibernate** is called, the device enters a deeper sleep state (the buffer can be cleared before hibernation); when **suspend** is called, the device enters a shallower low-power sleep state (the device enters sleep after the screen is turned off). Use **hibernate** when maximum power saving is required, and choose **suspend** when the device needs to resume activity quickly. This **hibernate** method is applicable to scenarios where the device is idle for a long time and requires deep power saving.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_MANAGER

For API versions 12 to 18, no permission is required to use this API. Starting from API version 19, the **ohos.permission.POWER_MANAGER** permission is required.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| clearMemory | boolean | Yes | Whether to clear the buffer before entering hibernation. The value **true** means to clear the buffer, and **false** means not to clear the buffer. |

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. <br>Applicable versions: 19+|
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 401     | Parameter error. Possible causes: 1. Parameter verification failed. |

**Example**

```js
try {
    power.hibernate(true);
} catch (err) {
    console.error(`Failed to hibernate device. Code: ${err.code}, message: ${err.message}`);
}
```

## power.refreshActivity<sup>20+</sup>

refreshActivity(reason: string): void

Refreshes the active state of the device. For example, resets the screen-off timeout duration.

This API takes effect only when the device is in the active state.

**System API**: This is a system API.

**Required permissions**: ohos.permission.REFRESH_USER_ACTION

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Device behavior differences:** When this API is called on a car device, error code 801 is returned. On other devices, it is called normally.

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| reason | string | Yes    | Reason for refreshing the active state of the device. It takes effect only when the device is in the active state. For details about the active state, see [power.isActive](js-apis-power.md#powerisactive9). |

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 4900201 |The device activity is being refreshed too frequently; the minimum time interval is 100 ms. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 801     | Capability not supported. This API cannot work in car devices.<br>Applicable versions: 26.0.1+ |

**Example**

```js
try {
    power.refreshActivity('refreshActivity_test');
} catch (err) {
    console.error(`Failed to refresh activity. Code: ${err.code}, message: ${err.message}`);
}
```

## power.setPowerKeyFilteringStrategy<sup>21+</sup>

setPowerKeyFilteringStrategy(strategy: PowerKeyFilteringStrategy): void

Sets the power key filtering strategy. After the power service subscribes to the power key event, this API is used to configure the processing mode of this event.

For details about the power key filtering strategy, see [power.PowerKeyFilteringStrategy](js-apis-power.md#powerkeyfilteringstrategy21).

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_MANAGER

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| strategy | [PowerKeyFilteringStrategy](js-apis-power.md#powerkeyfilteringstrategy21) | Yes | Power key filtering strategy, which is used to configure the handling method of power key events. For the meaning of each strategy, see [PowerKeyFilteringStrategy](js-apis-power.md#powerkeyfilteringstrategy21). |

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
} catch (err) {
    console.error(`Failed to set power key filtering strategy. Code: ${err.code}, message: ${err.message}`);
}
```

## power.registerShutdownCallback<sup>23+</sup>

registerShutdownCallback(callback: Callback&lt;boolean&gt;): void

Registers a callback for power shutdown or restart. This API uses an asynchronous callback to return the result. After registering a callback by calling this API, you can call [power.unregisterShutdownCallback](#powerunregistershutdowncallback23) to unregister the callback and release system resources when the callback is no longer needed.

**System API**: This is a system API.

**Required permissions**: ohos.permission.REBOOT

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
        console.info('device is reboot: ' + isReboot);
    });
    console.info('register shutdown callback success.');
} catch (err) {
    console.error(`Failed to register shutdown callback. Code: ${err.code}, message: ${err.message}`);
}
```

## power.unregisterShutdownCallback<sup>23+</sup>

unregisterShutdownCallback(callback?: Callback\<void>): void

Unregisters the callback for power shutdown or restart. This API uses a synchronous callback to return the result. This API must be used in pairs with [power.registerShutdownCallback](#powerregistershutdowncallback23). You must call **registerShutdownCallback** to register a callback before calling this API to unregister the callback.

**System API**: This is a system API.

**Required permissions**: ohos.permission.REBOOT

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                          |
| -------- | -------------------- | ---- | ---------------------------------------------- |
| callback | Callback&lt;void&gt; | No | Callback that returns no value. This callback is invoked after the unregistration succeeds. If this parameter is not passed, the unregistration still takes effect, but no callback notification is triggered. |

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
} catch (err) {
    console.error(`Failed to unregister shutdown callback. Code: ${err.code}, message: ${err.message}`);
}
```

## power.getPowerConfig

getPowerConfig(sceneName: string): string

Queries the power configuration value by scenario name. For example, this API is used when the system power management app needs to read the power configuration parameters of a specific scenario.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_CONFIG

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| sceneName | string | Yes | Name of the power configuration scenario. The value contains a maximum of 128 bytes. Empty strings are not supported. |

**Return value**

| Type    | Description        |
| ------ | ------------ |
| string | Power configuration value corresponding to the specified scenario name. The specific content of the configuration value depends on the queried scenario name. |

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 4900400 | Invalid parameter. Possible causes: <br>1. The sceneName parameter is an empty string; <br>2. The length of sceneName parameter exceeds 128 bytes. |
| 4900501 | Failed to read the power configuration value. |

**Example**

```js
try {
    let configVal = power.getPowerConfig('scene_name_test');
    console.info('get power config success, configVal: ' + configVal);
} catch (err) {
    console.error(`Failed to get power config. Code: ${err.code}, message: ${err.message}`);
}
```

## power.setPowerConfig

setPowerConfig(sceneName: string, value: string): void

Sets the power configuration value by scenario name. For example, this API is used when the system power management app needs to dynamically adjust the power configuration parameters of a specific scenario.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions**: ohos.permission.POWER_CONFIG

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| sceneName | string | Yes    | Name of the power configuration scenario. The value contains a maximum of 128 bytes. Empty strings are not supported. |
| value | string | Yes    | Power configuration value. The value contains a maximum of 128 bytes. Empty strings are not supported. |

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 4900400 | Invalid parameter. Possible causes: <br>1. The sceneName or value parameter is an empty string; <br>2. The length of sceneName parameter exceeds 128 bytes; <br>3. The length of value parameter exceeds 128 bytes. |
| 4900601 | Failed to write the power configuration value. |

**Example**

```js
try {
    power.setPowerConfig('scene_name_test', 'value_test');
    console.info('set power config success');
} catch (err) {
    console.error(`Failed to set power config. Code: ${err.code}, message: ${err.message}`);
}
```