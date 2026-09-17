# startTimer (System API)

## Modules to Import

```TypeScript
import { systemTimer } from '@kit.BasicServicesKit';
```

## startTimer

```TypeScript
function startTimer(timer: number, triggerTime: number, callback: AsyncCallback<void>): void
```

Starts a timer. This API uses an asynchronous callback to return the result.

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timer | number | Yes | ID of the timer. |
| triggerTime | number | Yes | Time when the timer is triggered, in milliseconds.<br>If **TIMER_TYPE_REALTIME** is set as the timer type, the value of **triggerTime** is the system startup time, which can be obtained by calling [systemDateTime.getUptime(STARTUP)](arkts-basicservices-systemdatetime-getuptime-f.md).<br>If **TIMER_TYPE_REALTIME** is not set, the value of **triggerTime** is the wall time, which can be obtained by calling [systemDateTime.getTime()](arkts-basicservices-systemdatetime-gettime-f.md). |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
}
let triggerTime: number = new Date().getTime();
triggerTime += 3000;

try {
  systemTimer.createTimer(options).then((timerId: number) => {
    systemTimer.startTimer(timerId, triggerTime, (error: BusinessError) => {
      if (error) {
        console.error(`Failed to start timer. message: ${error.message}, code: ${error.code}`);
        return;
      }
      console.info(`Succeeded in starting the timer.`);
    });
    console.info(`Succeeded in creating a timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to create timer. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to create timer. message: ${error.message}, code: ${error.code}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
}
let triggerTime: number = new Date().getTime();
triggerTime += 3000;

try {
  systemTimer.createTimer(options).then((timerId: number) => {
    systemTimer.startTimer(timerId, triggerTime).then(() => {
      console.info(`Succeeded in starting the timer.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to start timer. message: ${error.message}, code: ${error.code}`);
    });
    console.info(`Succeeded in creating a timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to create timer. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to create timer. message: ${error.message}, code: ${error.code}`);
}
```


## startTimer

```TypeScript
function startTimer(timer: number, triggerTime: number): Promise<void>
```

Starts a timer. This API uses a promise to return the result.

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timer | number | Yes | ID of the timer. |
| triggerTime | number | Yes | Time when the timer is triggered, in milliseconds.<br>If **TIMER_TYPE_REALTIME** is set as the timer type, the value of **triggerTime** is the system startup time, which can be obtained by calling [systemDateTime.getUptime(STARTUP)](arkts-basicservices-systemdatetime-getuptime-f.md).<br>If **TIMER_TYPE_REALTIME** is not set, the value of **triggerTime** is the wall time, which can be obtained by calling [systemDateTime.getTime()](arkts-basicservices-systemdatetime-gettime-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameter types. |

**Examples**

See [startTimer](#starttimer)
