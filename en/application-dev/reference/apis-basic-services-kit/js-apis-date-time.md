# @ohos.systemDateTime (System Time and Time Zone)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Time-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @murphy1984-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=ab611c219b2bb1b484101433888e822b3807a11c translatedAt=2026-11-10T04:03:30.693Z pushedAt=2026-11-10T06:15:25.145Z nl=1 -->

This module mainly consists of system time and system time zone functions. Developers can obtain the system time (including the Unix epoch time and system boot time), system date, system time zone, and the switch state of automatic time setting. Both synchronous and asynchronous methods are supported. It is applicable to scenarios where the current time needs to be displayed in an application, time calculation needs to be performed, or time zone related services need to be handled.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { systemDateTime } from '@kit.BasicServicesKit';
```

## TimeType<sup>10+</sup>

Enumerates the types of time to obtain.

**System capability**: SystemCapability.MiscServices.Time

| Name   | Value  | Description                                            |
| ------- | ---- | ------------------------------------------------ |
| STARTUP | 0    | Time elapsed since system boot, including deep sleep time.   |
| ACTIVE  | 1    | Time elapsed since system boot, excluding deep sleep time. |

## systemDateTime.getCurrentTime<sup>(deprecated)</sup>

getCurrentTime(isNano: boolean, callback: AsyncCallback&lt;number&gt;): void

Obtains the time elapsed since the Unix epoch. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [systemDateTime.getTime<sup>10+</sup>](#systemdatetimegettime10) instead.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name  | Type      | Mandatory| Description                            |
| -------- | -------------- | ---- | ------------------ |
| isNano   | boolean                     | Yes  | Whether the time to return is in nanoseconds.<br>- **true**: The result is in nanoseconds.<br>- **false**: The result is in milliseconds.|
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the time elapsed since the Unix epoch.        |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                             |
| -------- |-------------------------------------------------------------------|
| 401       | Parameter error. Possible causes: 1.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getCurrentTime(true, (error: BusinessError, time: number) => {
    if (error) {
      console.error(`Failed to get currentTime. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in getting currentTime : ${time}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get currentTime. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getCurrentTime<sup>(deprecated)</sup>

getCurrentTime(callback: AsyncCallback&lt;number&gt;): void

Obtains the time elapsed since the Unix epoch. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [systemDateTime.getTime<sup>10+</sup>](#systemdatetimegettime10) instead.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name  | Type              | Mandatory| Description                           |
| -------- | ----------- | ---- | ---------------------------------- |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the time elapsed since the Unix epoch, in milliseconds.        |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code   | Error Message                                                             |
|----------|-------------------------------------------------------------------|
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getCurrentTime((error: BusinessError, time: number) => {
    if (error) {
      console.error(`Failed to get currentTime. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in getting currentTime : ${time}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get currentTime. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getCurrentTime<sup>(deprecated)</sup>

getCurrentTime(isNano?: boolean): Promise&lt;number&gt;

Obtains the time elapsed since the Unix epoch. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [systemDateTime.getTime<sup>10+</sup>](#systemdatetimegettime10) instead.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name| Type   | Mandatory| Description                    |
| ------ | ------- | ---- | ------------------------- |
| isNano | boolean | No | Whether the return result is in nanoseconds. The default value is false.<br>- true: the result is in nanoseconds (ns). <br>- false: the result is in milliseconds (ms). |

**Return value**

| Type       | Description                              |
| --------------------- | --------------------------- |
| Promise&lt;number&gt; | Promise used to return the timestamp that has elapsed since the Unix epoch.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message                                                             |
|---------|-------------------------------------------------------------------|
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getCurrentTime().then((time: number) => {
    console.info(`Succeeded in getting currentTime : ${time}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get currentTime. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get currentTime. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getRealActiveTime<sup>(deprecated)</sup>

getRealActiveTime(isNano: boolean, callback: AsyncCallback&lt;number&gt;): void

Obtains the time elapsed since system startup, excluding the deep sleep time. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [systemDateTime.getUptime<sup>10+</sup>](#systemdatetimegetuptime10) instead.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name  | Type                       | Mandatory| Description  |
| -------- | ---------- | ---- | -------------------------- |
| isNano   | boolean                     | Yes   | Whether the return result is in nanoseconds.<br>- true: the return result is in nanoseconds (ns). <br>- false: the return result is in milliseconds (ms). |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the time.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message                                                             |
|---------|-------------------------------------------------------------------|
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getRealActiveTime(true, (error: BusinessError, time: number) => {
    if (error) {
      console.error(`Failed to get real active time. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in getting real active time : ${time}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get real active time. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getRealActiveTime<sup>(deprecated)</sup>

getRealActiveTime(callback: AsyncCallback&lt;number&gt;): void

Obtains the time elapsed since system startup, excluding the deep sleep time. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [systemDateTime.getUptime<sup>10+</sup>](#systemdatetimegetuptime10) instead.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name  | Type                       | Mandatory| Description   |
| -------- | -------------- | ---- | --------------------- |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the time.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message                                                             |
|---------|-------------------------------------------------------------------|
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getRealActiveTime((error: BusinessError, time: number) => {
    if (error) {
      console.error(`Failed to get real active time. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in getting real active time : ${time}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get real active time. Code: ${error.code}, message: ${error.message}`);
}
```


## systemDateTime.getRealActiveTime<sup>(deprecated)</sup>
getRealActiveTime(isNano?: boolean): Promise&lt;number&gt;

Obtains the time elapsed since system startup, excluding the deep sleep time. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [systemDateTime.getUptime<sup>10+</sup>](#systemdatetimegetuptime10) instead.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name| Type   | Mandatory| Description                             |
| ------ | ------- | ---- | ----------------------------------- |
| isNano | boolean | No | Whether the return result is in nanoseconds. The default value is **false**.<br>- **true**: The result is in nanoseconds (ns). <br>- **false**: The result is in milliseconds (ms). |

**Return value**

| Type                 | Description        |
| -------------- | -------------------------------- |
| Promise&lt;number&gt; | Promise used to return the time elapsed since system startup, excluding the deep sleep time.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message                                                             |
|---------|-------------------------------------------------------------------|
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getRealActiveTime().then((time: number) => {
    console.info(`Succeeded in getting real active time : ${time}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get real active time. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get real active time. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getRealTime<sup>(deprecated)</sup>

getRealTime(isNano: boolean, callback: AsyncCallback&lt;number&gt;): void

Obtains the time elapsed since system startup, including the deep sleep time. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [systemDateTime.getUptime<sup>10+</sup>](#systemdatetimegetuptime10) instead.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name  | Type                       | Mandatory| Description  |
| -------- | --------------- | ---- | ------------------------------- |
| isNano   | boolean                     | Yes   | Whether the return result is nanoseconds.<br>- true: the result is nanoseconds (ns). <br>- false: the result is milliseconds (ms). |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the time.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message                                                             |
|---------|-------------------------------------------------------------------|
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getRealTime(true, (error: BusinessError, time: number) => {
    if (error) {
      console.error(`Failed to get real time. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in getting real time : ${time}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get real time. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getRealTime<sup>(deprecated)</sup>

getRealTime(callback: AsyncCallback&lt;number&gt;): void

Obtains the time elapsed since system startup, including the deep sleep time. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [systemDateTime.getUptime<sup>10+</sup>](#systemdatetimegetuptime10) instead.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name  | Type                       | Mandatory| Description     |
| -------- | --------- | ---- | --------------------------- |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the result.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message                                                             |
|---------|-------------------------------------------------------------------|
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getRealTime((error: BusinessError, time: number) => {
    if (error) {
      console.error(`Failed to get real time. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in getting real time : ${time}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get real time. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getRealTime<sup>(deprecated)</sup>

getRealTime(isNano?: boolean): Promise&lt;number&gt;

Obtains the time elapsed since system startup, including the deep sleep time. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [systemDateTime.getUptime<sup>10+</sup>](#systemdatetimegetuptime10) instead.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name| Type   | Mandatory| Description                              |
| ------ | ------- | ---- | ------------------------------- |
| isNano | boolean | No | Whether the return result is in nanoseconds. The default value is **false**.<br>- **true**: the return result is in nanoseconds (ns). <br>- **false**: the return result is in milliseconds (ms). |

**Return value**

| Type                 | Description      |
| --------------------- | ------------------------------- |
| Promise&lt;number&gt; | Promise used to return the time elapsed since system startup, including the deep sleep time.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message                                                             |
|---------|-------------------------------------------------------------------|
| 401     | Parameter error. Possible causes: 1.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getRealTime().then((time: number) => {
    console.info(`Succeeded in getting real time : ${time}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get real time. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get real time. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getTime<sup>10+</sup>

getTime(isNanoseconds?: boolean): number

Obtains the time elapsed since the Unix epoch to the current system time. This API uses synchronous mode.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name       | Type   | Mandatory| Description                                                        |
| ------------- | ------- | ---- | ------------------------------------------------------------ |
| isNanoseconds | boolean | No  | Whether the time to return is in nanoseconds.<br>- **true**: The result is in nanoseconds.<br>- **false**: The result is in milliseconds.<br>The default value is **false**.|

**Return value**

| Type  | Description                      |
| ------ | -------------------------- |
| number | Time elapsed since the Unix epoch.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let time: number = systemDateTime.getTime(true);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get time. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getUptime<sup>10+</sup>

getUptime(timeType: TimeType, isNanoseconds?: boolean): number

Obtains the time elapsed since system boot in synchronous mode. Based on TimeType, you can obtain the total boot duration including deep sleep time (STARTUP, applicable to scenarios such as counting the total device running time) or the active running duration excluding deep sleep time (ACTIVE, applicable to scenarios such as performance monitoring and active duration statistics).

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name       | Type                   | Mandatory| Description                                                                               |
| ------------- | ----------------------- | ---- |-----------------------------------------------------------------------------------|
| timeType      | [TimeType](#timetype10) | Yes  | Type of the time to be obtained. The value can only be `STARTUP` or `ACTIVE`.                                                 |
| isNanoseconds | boolean | No | Whether the return result is in nanoseconds.<br>- true: the result is in nanoseconds (ns).<br>- false: the result is in milliseconds (ms).<br>Default value is false. |

**Return value**

| Type  | Description                      |
| ------ | -------------------------- |
| number | Time elapsed since system startup.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                                                                          |
| -------- |----------------------------------------------------------------------------------------------------------------|
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.<br>Applicable versions: 12 and later |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let time: number = systemDateTime.getUptime(systemDateTime.TimeType.ACTIVE, false);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get uptime. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getDate<sup>(deprecated)</sup>

getDate(callback: AsyncCallback&lt;Date&gt;): void

Obtains the current system date. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> Supported since API version 9 and deprecated since API version 10. It is recommended to use the `new Date()` method instead (for details, see the document "How to Convert a Time-Format String to a Date Object"). `new Date()` returns a `Date` instance.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name  | Type          | Mandatory| Description                  |
| -------- | -------------- | ---- | --------------------- |
| callback | AsyncCallback&lt;Date&gt; | Yes  | Callback used to return the current system date.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                |
|-------|------------------------------------------------------|
| 401   | Parameter error. Possible causes: 1.System error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getDate((error: BusinessError, date: Date) => {
    if (error) {
      console.error(`Failed to get date. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in getting date : ${date}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get date. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getDate<sup>(deprecated)</sup>

getDate(): Promise&lt;Date&gt;

Obtains the current system date. This API uses a promise to return the result.

> **Note:** Supported since API version 9 and deprecated since API version 10. It is recommended to use the `new Date()` method instead (for details, see the document "How to Convert a Time-Format String to a Date Object"). `new Date()` returns a `Date` instance.

**System capability**: SystemCapability.MiscServices.Time

**Return value**

| Type               | Description                                     |
| ------------------- | ----------------------------------------- |
| Promise&lt;Date&gt; | Promise used to return the current system date.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                |
|-------|------------------------------------------------------|
| 401   | Parameter error. Possible causes: 1.System error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getDate().then((date: Date) => {
    console.info(`Succeeded in getting date : ${date}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get date. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get date. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getTimezone

getTimezone(callback: AsyncCallback&lt;string&gt;): void

Obtains the system time zone. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.Time

**Parameters**

| Name  | Type             | Mandatory| Description                |
| -------- | --------- | ---- | ------------------------ |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the system time zone. For details, see [Supported System Time Zones](#supported-system-time-zones).|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getTimezone((error: BusinessError, timezone: string) => {
    if (error) {
      console.error(`Failed to get timezone. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in getting timezone: ${timezone}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get timezone. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getTimezone

getTimezone(): Promise&lt;string&gt;

Obtains the system time zone. This API uses a promise to return the result.

**System capability**: SystemCapability.MiscServices.Time

**Return value**

| Type                 | Description                                 |
| --------------------- | ------------------------------------- |
| Promise&lt;string&gt; | Promise used to return the system time zone. For details, see [Supported System Time Zones](#supported-system-time-zones).|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getTimezone().then((timezone: string) => {
    console.info(`Succeeded in getting timezone: ${timezone}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get timezone. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get timezone. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getTimezoneSync<sup>10+</sup>

getTimezoneSync(): string

Obtains the system time zone in synchronous mode.

**System capability**: SystemCapability.MiscServices.Time

**Return value**

| Type  | Description                                                      |
| ------ | ---------------------------------------------------------- |
| string | System time zone. For details, see [Supported System Time Zones](#supported-system-time-zones).|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let timezone: string = systemDateTime.getTimezoneSync();
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get timezone. Code: ${error.code}, message: ${error.message}`);
}
```

## Supported System Time Zones

The following table lists the supported system time zones and the respective standard time offset (unit: h) between each time zone and time zone 0.

| Time Zone                          | Offset        |
| ------------------------------ | --------------------- |
| Antarctica/McMurdo             | 12                    |
| America/Argentina/Buenos_Aires | -3                    |
| Australia/Sydney               | 10                    |
| America/Noronha                | -2                    |
| America/St_Johns               | -3.5                  |
| Africa/Kinshasa                | 1                     |
| America/Santiago               | -4                    |
| Asia/Shanghai                  | 8                     |
| Asia/Nicosia                   | 2                     |
| Europe/Berlin                  | 2                     |
| America/Guayaquil              | -5                    |
| Europe/Madrid                  | 2                     |
| Pacific/Pohnpei                | 11                    |
| America/Godthab                | -2                    |
| Asia/Jakarta                   | 7                     |
| Pacific/Tarawa                 | 12                    |
| Asia/Almaty                    | 6                     |
| Pacific/Majuro                 | 12                    |
| Asia/Ulaanbaatar               | 8                     |
| America/Mexico_City            | -6                    |
| Asia/Kuala_Lumpur              | 8                     |
| Pacific/Auckland               | 12                    |
| Pacific/Tahiti                 | -10                   |
| Pacific/Port_Moresby           | 10                    |
| Asia/Gaza                      | 2                     |
| Europe/Lisbon                  | 0                     |
| Europe/Moscow                  | 3                     |
| Europe/Kiev                    | 2                     |
| Pacific/Wake                   | 12                    |
| America/New_York               | -5                    |
| Asia/Tashkent                  | 5                     |

## systemDateTime.getAutoTimeStatus<sup>21+</sup>

getAutoTimeStatus(): boolean

Obtains the switch status of the automatic time setting. This API returns the result synchronously.

**System capability**: SystemCapability.MiscServices.Time

**Return value**

| Type  | Description                                                      |
| ------ | ---------------------------------------------------------- |
| boolean | Switch status of the automatic time setting.<br>- true: The automatic time setting is on.<br>- false: The automatic time setting is off. |

**Error codes**

For details about the error codes, see [Time and Time Zone Service Error Codes](./errorcode-time.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                                                                   |
|-------|-------------------------------------------------------------------------------------------------------------|
| 13000001    | Network connection error or OS error. Possible causes: 1.System memory is insufficient; 2.Calls the underlying system interface failed.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let status: boolean = systemDateTime.getAutoTimeStatus();
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get autotime status. Code: ${error.code}, message: ${error.message}`);
}
```
