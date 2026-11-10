# @ohos.systemTimer (System Timer)(System API)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Time-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=ab611c219b2bb1b484101433888e822b3807a11c translatedAt=2026-11-10T04:15:42.654Z pushedAt=2026-11-10T07:05:48.272Z nl=1 -->

This module mainly consists of the system timer functions. It provides the capabilities of creating, starting, stopping, and destroying timers, and supports creating multiple timer types such as the system startup time timer, wakeup timer, exact timer, and IDLE mode timer. Developers can use the timer functions to implement scheduled services, such as alarm clocks. The typical usage flow of a timer is as follows: first create a timer through createTimer, then start the timer through startTimer, stop the timer through stopTimer as needed, and finally destroy the timer through destroyTimer to release resources.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.

## Modules to Import


```ts
import { systemTimer } from '@kit.BasicServicesKit';
```

## Constants

Enumerates the timer types that can be created.

**System capability**: SystemCapability.MiscServices.Time

| Name                | Type   | Value | Description                                          |
| ------------------- | ------ | ---- |---------------------------------------------|
| TIMER_TYPE_REALTIME | number | 1    | System startup time timer (the timer start time cannot be later than the currently set system time).|
| TIMER_TYPE_WAKEUP   | number | 2    | Wakeup timer (if it is not configured as a wakeup timer, it will not be triggered when the system is in sleep state until the system exits the sleep state).|
| TIMER_TYPE_EXACT    | number | 4    | Exact timer (when the system time is changed, an offset error of up to 1s may occur).|
| TIMER_TYPE_IDLE     | number | 8    | IDLE mode timer (supported only for system service configuration, not for application configuration).|

## TimerOptions

Defines the initialization options for creating a system timer.

**System capability**: SystemCapability.MiscServices.Time

| Name | Type | Read-Only | Optional | Description |
|------|------|------|------|-------------------------------|
| type | number | No | No | Timer type, which can be selected from multiple options using '\|'.<br>The value **1** indicates a system startup time timer (the timer start time cannot be later than the currently set system time).<br>The value **2** indicates a wakeup timer (if the timer is not configured as a wakeup timer, it will not be triggered while the system is in sleep state until the system exits the sleep state).<br>The value **4** indicates an exact timer (when the app is frozen, the timer is also frozen, and the timer is subject to unified heartbeat control; therefore, even an exact timer cannot be guaranteed to trigger at the specified time point; if the system time is changed, an offset error of up to 1s may occur).<br>The value **8** indicates an IDLE mode timer (supported only for system service configuration, not for application configuration). |
| repeat | boolean | No | No | Whether the timer is a repeating timer. The value **true** indicates a repeating timer, and **false** indicates a one-shot timer. |
| autoRestore<sup>15+</sup> | boolean | No | Yes | Whether to restore the timer after the device restarts.<br>The value **true** indicates that the timer is restored after restart, and **false** indicates that it is not restored after restart.<br>Only timers that are not of the `TIMER_TYPE_REALTIME` type and are configured with a wantAgent can be set to **true**. If this condition is not met, this parameter does not take effect.<br>The default value is **false**. |
| name<sup>15+</sup> | string | No | Yes | Timer name, which cannot exceed 64 bytes. If the length limit is exceeded, timer creation fails and an error is returned.<br>Two timers with the same name cannot exist simultaneously under the same UID. If a timer is created with the same name as a previously created timer, the previously created timer will be destroyed.<br>The default value is an empty string. |
| interval | number | No | Yes | Timer interval, in milliseconds.<br>For a repeating timer, the minimum value of **interval** is 1s and the maximum value is 365 days. It is recommended that the value of **interval** be no less than 5000 milliseconds. If the value is out of this range, timer creation fails and an error is returned.<br>For a one-shot timer, the value of **interval** is 0.<br>The default value is 0. |
| wantAgent | WantAgent | No | Yes | WantAgent for setting the notification. After the timer expires, a notification is sent (starting the application MainAbility is supported, but starting ServiceAbility is not supported).<br>The default value is empty. |
| callback | function | No | Yes | Callback function to be executed by the user, which is invoked when the timer is triggered. Pass this parameter when custom logic needs to be executed when the timer is triggered. If this parameter is not passed, it defaults to empty, and no user-defined logic is executed after the timer is triggered. |


## systemTimer.createTimer

createTimer(options: TimerOptions, callback: AsyncCallback&lt;number&gt;): void

Creates a timer. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API must be used together with [systemTimer.destroyTimer](#systemtimerdestroytimer). Otherwise, memory leaks may occur.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name     | Type                          | Mandatory | Description                                                         |
| -------- | ----------------------------- | --------- | ------------------------------------------------------------ |
| options  | [TimerOptions](#timeroptions) | Yes       | Initialization options for creating a system timer, including the timer type, whether to trigger repeatedly, the interval, and the WantAgent notification mechanism. |
| callback | AsyncCallback&lt;number>      | Yes       | Callback invoked to return the timer ID.                                   |

**Error codes**

For details about the following error codes, see [Time and Time Zone Service Error Codes](./errorcode-time.md).

| ID | Error Message                                                                                                                                         |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------|
| 202   | Permission verification failed. A non-system application calls a system API.                                                                 |
| 401   | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat: false
};
try {
  systemTimer.createTimer(options, (error: BusinessError, timerId: number) => {
    if (error) {
      console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
}
```

## systemTimer.createTimer

createTimer(options: TimerOptions): Promise&lt;number&gt;

Creates a timer. This API uses a promise to return the timer ID.

> **NOTE**
> 
> This API must be used together with [systemTimer.destroyTimer](#systemtimerdestroytimer). Otherwise, memory leaks may occur.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name | Type                          | Mandatory | Description                                                         |
| ------- | ----------------------------- | ---- | ------------------------------------------------------------ |
| options | [TimerOptions](#timeroptions) | Yes  | Initialization options for creating a system timer, including the timer type, whether to trigger repeatedly, interval, and WantAgent notification mechanism. |

**Return value**

| Type                  | Description                          |
| --------------------- | ----------------------------- |
| Promise&lt;number&gt; | Promise used to return the timer ID. |

**Error codes**

For details about the following error codes, see [Time and Time Zone Service Error Codes](./errorcode-time.md).

| ID | Error Message                                                                                                        |
|-------|-------------------------------------------------------------------------------------------------------------|
| 202   | Permission verification failed. A non-system application calls a system API.                                |
| 401   | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
};
try {
  systemTimer.createTimer(options).then((timerId: number) => {
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
}
```

## systemTimer.startTimer

startTimer(timer: number, triggerTime: number, callback: AsyncCallback&lt;void&gt;): void

Starts a timer. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API must be used together with [systemTimer.stopTimer](#systemtimerstoptimer) to stop the started timer. The typical calling sequence is createTimer → startTimer → stopTimer → destroyTimer.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name | Type                   | Mandatory | Description                                                                                                                                                                                                                                                           |
| -------------- | ---------------------- | --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| timer          | number                 | Yes       | ID of the timer.                                                                                                                                                                                                                                                      |
| triggerTime    | number                 | Yes       | Trigger time of the timer, in milliseconds.<br>If the timer type includes TIMER_TYPE_REALTIME, this triggerTime should be the system startup time. It is recommended to obtain it through [systemDateTime.getUptime()](js-apis-date-time.md#systemdatetimegetuptime10); otherwise, the timer cannot be triggered at the expected time.<br>If the timer type does not include TIMER_TYPE_REALTIME, this triggerTime should be the wall clock time. It is recommended to obtain it through [systemDateTime.getTime()](js-apis-date-time.md#systemdatetimegettime10); otherwise, the timer cannot be triggered at the expected time. |
| callback       | AsyncCallback&lt;void> | Yes       | Callback used to receive the timer start result. The callback parameter is err (an error object, which is undefined when the timer is started successfully).                                                                                                                                 |

**Error codes**

For details about the following error codes, see [Time and Time Zone Service Error Codes](./errorcode-time.md).

| ID | Error Message                                                                                                        |
|-------|-------------------------------------------------------------------------------------------------------------|
| 202   | Permission verification failed. A non-system application calls a system API.                                |
| 401   | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
};
let triggerTime: number = new Date().getTime();
triggerTime += 3000;

try {
  systemTimer.createTimer(options).then((timerId: number) => {
    systemTimer.startTimer(timerId, triggerTime, (error: BusinessError) => {
      if (error) {
        console.error(`Failed to start timer. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info(`Succeeded in starting timer.`);
    });
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to start timer. Code: ${error.code}, message: ${error.message}`);
}
```

## systemTimer.startTimer

startTimer(timer: number, triggerTime: number): Promise&lt;void&gt;

Starts the timer. This API uses a promise to return the result.

> **NOTE**
>
> This API must be used with [systemTimer.stopTimer](#systemtimerstoptimer) to stop the started timer. The typical calling sequence is createTimer → startTimer → stopTimer → destroyTimer.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name        | Type   | Mandatory | Description                                                                                                                                                                                                                                                           |
| ----------- | ------ | --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| timer       | number | Yes       | Timer ID.                                                                                                                                                                                                                                                      |
| triggerTime | number | Yes       | Trigger time of the timer, in milliseconds.<br>If the timer type includes TIMER_TYPE_REALTIME, this triggerTime should be the system startup time. It is recommended to obtain it via [systemDateTime.getUptime()](js-apis-date-time.md#systemdatetimegetuptime10); otherwise the timer cannot be triggered at the expected time.<br>If the timer type does not include TIMER_TYPE_REALTIME, this triggerTime should be the wall clock time. It is recommended to obtain it via [systemDateTime.getTime()](js-apis-date-time.md#systemdatetimegettime10); otherwise the timer cannot be triggered at the expected time. |

**Return value**

| Type           | Description                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value. resolve indicates that the timer is started successfully, and reject indicates that the timer fails to be started. |

**Error codes**

For details about the following error codes, see [Time and Time Zone Service Error Codes](./errorcode-time.md).

| ID | Error Message                                                                                                        |
|-------|-------------------------------------------------------------------------------------------------------------|
| 202   | Permission verification failed. A non-system application calls a system API.                                |
| 401   | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
};
let triggerTime: number = new Date().getTime();
triggerTime += 3000;

try {
  systemTimer.createTimer(options).then((timerId: number) => {
    systemTimer.startTimer(timerId, triggerTime).then(() => {
      console.info(`Succeeded in starting timer.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to start timer. Code: ${error.code}, message: ${error.message}`);
    });
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
}
```

## systemTimer.stopTimer

stopTimer(timer: number, callback: AsyncCallback&lt;void&gt;): void

Stops a timer. This API uses an asynchronous callback to return the result. It must be used with [systemTimer.startTimer](#systemtimerstarttimer) to stop a started timer. After the timer is stopped, you can call [systemTimer.destroyTimer](#systemtimerdestroytimer) to destroy the timer and release resources.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name | Type                   | Mandatory | Description         |
| -------- | ---------------------- | ---- | ------------ |
| timer    | number                 | Yes   | Timer ID. |
| callback | AsyncCallback&lt;void> | Yes   | Callback function used to receive the result of stopping the timer. The callback parameter err is an error object, which is undefined if the timer is stopped successfully.   |

**Error codes**

For details about the following error codes, see [Time and Time Zone Service Error Codes](./errorcode-time.md).

| ID | Error Message                                                                                                        |
|-------|-------------------------------------------------------------------------------------------------------------|
| 202   | Permission verification failed. A non-system application calls a system API.                                |
| 401   | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
};
let triggerTime: number = new Date().getTime();
triggerTime += 3000;

try {
  systemTimer.createTimer(options).then((timerId: number) => {
    systemTimer.startTimer(timerId, triggerTime);
    systemTimer.stopTimer(timerId, (error: BusinessError) => {
      if (error) {
        console.error(`Failed to stop timer. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info(`Succeeded in stopping timer.`);
    });
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to stop timer. Code: ${error.code}, message: ${error.message}`);
}
```

## systemTimer.stopTimer

stopTimer(timer: number): Promise&lt;void&gt;

Stops a timer. This API uses a promise to return the result asynchronously. It must be used together with [systemTimer.startTimer](#systemtimerstarttimer) to stop a started timer. After the timer is stopped, you can call [systemTimer.destroyTimer](#systemtimerdestroytimer) to destroy the timer and release resources.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name | Type   | Mandatory | Description |
| ------ | ------ | ---- | ------------ |
| timer  | number | Yes  | Timer ID. |

**Return value**

| Type           | Description                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value. The promise is resolved when the timer is stopped successfully and rejected when the timer fails to be stopped. |

**Error codes**

For details about the following error codes, see [Time and Time Zone Service Error Codes](./errorcode-time.md).

| ID | Error Message                                                                                                        |
|-------|-------------------------------------------------------------------------------------------------------------|
| 202   | Permission verification failed. A non-system application calls a system API.                                |
| 401   | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
};
let triggerTime: number = new Date().getTime();
triggerTime += 3000;

try {
  systemTimer.createTimer(options).then((timerId: number) => {
    systemTimer.startTimer(timerId, triggerTime);
    systemTimer.stopTimer(timerId).then(() => {
      console.info(`Succeeded in stopping timer.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to stop timer. Code: ${error.code}, message: ${error.message}`);
    });
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to operate timer. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to stop timer. Code: ${error.code}, message: ${error.message}`);
}
```

## systemTimer.destroyTimer

destroyTimer(timer: number, callback: AsyncCallback&lt;void&gt;): void

Destroys a timer. This API uses an asynchronous callback.

> **NOTE**
>
> This API must be used with [systemTimer.createTimer](#systemtimercreatetimer) to destroy the timer created by createTimer and avoid memory leaks. It is recommended to call [systemTimer.stopTimer](#systemtimerstoptimer) to stop the timer before destroying it.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name | Type                   | Mandatory | Description         |
| -------- | ---------------------- | ---- | ------------ |
| timer    | number                 | Yes   | Timer ID. |
| callback | AsyncCallback&lt;void> | Yes   | Callback used to receive the timer destruction result. The callback parameter is err (an error object, which is undefined when the destruction succeeds).   |

**Error codes**

For details about the following error codes, see [Time and time zone service error codes](./errorcode-time.md).

| ID | Error Message                                                                                                        |
|-------|-------------------------------------------------------------------------------------------------------------|
| 202   | Permission verification failed. A non-system application calls a system API.                                |
| 401   | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
};
let triggerTime: number = new Date().getTime();
triggerTime += 3000;

try {
  systemTimer.createTimer(options).then((timerId: number) => {
    systemTimer.startTimer(timerId, triggerTime);
    systemTimer.stopTimer(timerId);
    systemTimer.destroyTimer(timerId, (error: BusinessError) => {
      if (error) {
        console.error(`Failed to destroy timer. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info(`Succeeded in destroying timer.`);
    });
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to operate timer. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to destroy timer. Code: ${error.code}, message: ${error.message}`);
}
```

## systemTimer.destroyTimer

destroyTimer(timer: number): Promise&lt;void&gt;

Destroys a timer. This API uses a promise to perform asynchronous callback. It must be used together with [systemTimer.createTimer](#systemtimercreatetimer) to destroy the timer created by createTimer and avoid memory leaks. It is recommended to call [systemTimer.stopTimer](#systemtimerstoptimer) to stop the timer before destroying it.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name | Type   | Mandatory | Description |
| ------ | ------ | ---- | ------------ |
| timer  | number | Yes   | Timer ID. |

**Return value**

| Type           | Description                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value. resolve indicates that the timer is destroyed successfully, and reject indicates that destruction fails. |

**Error codes**

For details about the following error codes, see [Time Zone Service Error Codes](./errorcode-time.md).

| ID | Error Message                                                                                                        |
|-------|-------------------------------------------------------------------------------------------------------------|
| 202   | Permission verification failed. A non-system application calls a system API.                                |
| 401   | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
};
let triggerTime: number = new Date().getTime();
triggerTime += 3000;

try {
  systemTimer.createTimer(options).then((timerId: number) => {
    systemTimer.startTimer(timerId, triggerTime);
    systemTimer.stopTimer(timerId);
    systemTimer.destroyTimer(timerId).then(() => {
      console.info(`Succeeded in destroying timer.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to destroy timer. Code: ${error.code}, message: ${error.message}`);
    });
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to operate timer. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to destroy timer. Code: ${error.code}, message: ${error.message}`);
}
```