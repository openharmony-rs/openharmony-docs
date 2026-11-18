# @ohos.power (Power Management)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=b059b47d399447b512910e67cfcc81779f08ec3f translatedAt=2026-11-06T01:42:02.566Z pushedAt=2026-11-09T03:13:44.641Z nl=1 -->

This module provides APIs for querying the screen status, querying the power mode, and detecting the standby mode. It also provides the capability of configuring the power key filtering policy. You can use the APIs of this module to obtain the active state, power mode, screen on/off state, and standby low-power state of a device. These APIs are applicable to scenarios where service logic needs to be adjusted based on the device power state, for example, restricting background activities in low-power mode and optimizing battery life strategies in standby mode.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { power } from '@kit.BasicServicesKit';
```

## power.isActive<sup>9+</sup>

isActive(): boolean

Checks whether the current device is in the active state. This API can be used to adjust their behavior based on the device active state, for example, pausing background tasks when the device is inactive.
- A device with a screen is active when the screen is on and inactive when the screen is off.
- A device without a screen is active when it exits the sleep mode and inactive when it enters the sleep mode.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Returns**

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| boolean | The value **true** is returned if the device is active; **false** is returned if the device is inactive or the device activity status fails to be obtained. |

**Example**

```js
let isActive = power.isActive();
console.info('power is active: ' + isActive);
```

## power.rebootDevice<sup>(deprecated)</sup>

rebootDevice(reason: string): void

Restart the device.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9<!--Del-->. You are advised to use [power.reboot](js-apis-power-sys.md#powerreboot9)<!--DelEnd--> instead. The substitute API is available only to system apps.

**Required permissions:** ohos.permission.REBOOT (available only to system apps).

**System capability**: SystemCapability.PowerManager.PowerManager.Core


**Parameters**

| Name   | Type    | Mandatory  | Description   |
| ------ | ------ | ---- | ----- |
| reason | string | Required | Reason for the restart. For example, **updater** indicates that the system enters the update mode after the restart. If no specific reason is specified, the system enters the normal mode after the restart. |

**Example**

```js
power.rebootDevice('reboot_test');
```

## power.getPowerMode<sup>9+</sup>

getPowerMode(): DevicePowerMode

Obtains the power mode of the current device. Different power modes correspond to different device behavior policies. You can adjust app behavior based on the returned mode value to adapt to the current mode. For the definition and description of each mode, see [DevicePowerMode](#devicepowermode9).

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Returns**

| Type                                | Description      |
| ------------------------------------ | ---------- |
| [DevicePowerMode](#devicepowermode9) | Power mode of the current device. The value can be standard mode, power saving mode, performance mode, or super power saving mode. If the power mode of the current device fails to be obtained, **0** is returned, which is not an enumerated value of [DevicePowerMode](#devicepowermode9). You should check whether the return value is a valid enumerated value (600 or greater). |

**Example**

```js
let mode = power.getPowerMode();
console.info('power mode: ' + mode);
```

## power.isStandby<sup>10+</sup>

isStandby(): boolean

Checks whether the current device enters the standby low-power mode. In standby mode, the system adopts power-saving policies. You should adjust the background tasks and resource usage policies of apps accordingly to avoid performing high-power operations in standby mode.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Returns**

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| boolean | The value **true** is returned if the device enters standby mode; **false** otherwise. |

**Error codes**

For details about the error codes, see [Power Manager Error Codes](errorcode-power.md).

| ID  | Error Message   |
|---------|---------|
| 4900101 | Failed to connect to the service. |

**Example**

```js
try {
    let isStandby = power.isStandby();
    console.info('device is in standby: ' + isStandby);
} catch (err) {
    console.error(`Failed to check isStandby. Code: ${err.code}, message: ${err.message}`);
}
```

## power.isScreenOn<sup>(deprecated)</sup>

isScreenOn(callback: AsyncCallback&lt;boolean&gt;): void

Checks the screen status of the current device. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [power.isActive](#powerisactive9) instead.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name  | Type                        | Mandatory| Description                                                        |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;boolean&gt; | Required | Callback used to return the result. If the detection succeeds, **err** is **undefined** and **data** is the obtained screen status, where **true** indicates the screen is on and **false** indicates the screen is off; otherwise, **err** is an error object. |

**Example**

```js
power.isScreenOn((err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`Failed to check screen status. Code: ${err.code}, message: ${err.message}`);
        return;
    }
    console.info('screen on status is ' + data);
});
```

## power.isScreenOn<sup>(deprecated)</sup>

isScreenOn(): Promise&lt;boolean&gt;

Checks the screen status of the current device. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [power.isActive](#powerisactive9) instead.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Returns**
| Type                  | Description                                              |
| ---------------------- | -------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the screen is on, and the value **false** indicates the opposite.|

**Example**

```js
power.isScreenOn()
.then((data: boolean) => {
    console.info('screen on status is ' + data);
})
.catch((err: BusinessError) => {
    console.error(`Failed to check screen status. Code: ${err.code}, message: ${err.message}`);
});
```

## DevicePowerMode<sup>9+</sup>

Enumerates power modes.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

| Name                   | Value  | Description                  |
| ----------------------- | ---- | ---------------------- |
| MODE_NORMAL             | 600  | Standard mode. It is the default value.|
| MODE_POWER_SAVE         | 601  | Power saving mode.        |
| MODE_PERFORMANCE        | 602  | Performance mode.        |
| MODE_EXTREME_POWER_SAVE | 603  | Ultra power saving mode.    |
| MODE_CUSTOM_POWER_SAVE<sup>20+</sup>  | 650  | Custom power saving mode.    |

## PowerKeyFilteringStrategy<sup>21+</sup>

Enumerates the power key filtering strategies.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

| Name                   | Value  | Description                  |
| ----------------------- | ---- | ---------------------- |
| DISABLE_LONG_PRESS_FILTERING | 0  | Indicates that the filtering policy for the power key long-press event is disabled. This is the default value. |
| LONG_PRESS_FILTERING_ONCE | 1  | Filters the long-press event of the current power key once.|