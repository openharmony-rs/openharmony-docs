# @ohos.systemDateTime (System Time and Time Zone) (System API)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Time-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=529d313a2a705ff7814d678d6d59d82297398d21 translatedAt=2026-11-10T04:17:18.238Z pushedAt=2026-11-10T07:05:11.193Z nl=1 -->

This module mainly consists of the system time and system time zone functions. Developers can set and obtain the system time and system time zone, update the network time through an NTP server, set the automatic time switch status, and so on. It is applicable to system application scenarios that require precise management of the system time and time zone.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This page contains only the system APIs of this module. For details about other public APIs, see [System Time and Time Zone](js-apis-date-time.md).

## Modules to Import

```ts
import { systemDateTime } from '@kit.BasicServicesKit';
```

## systemDateTime.setTime

setTime(time : number, callback : AsyncCallback&lt;void&gt;) : void

Sets the system time. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.Time

**Required permissions**: ohos.permission.SET_TIME

**Parameters**

| Name  | Type           | Mandatory| Description                                      |
| -------- | ----------- | ---- | ---------------- |
| time     | number                    | Yes  | Target timestamp (ms), which must be greater than 0. |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result of setting the system time. If the setting is successful, err is undefined; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                                                                       |
| -------- |-------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                          |
| 202       | Permission verification failed. A non-system application calls a system API.                                |
| 204       | Access denied due to user access control policy. Possible causes: 1.The operation is restricted by the OS-account constraint. 2.The required privilege for the operation has not been granted.<br>Applicable version: 26.0.0+ |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Set the system time to 2021-01-20 02:36:25.
let time: number = 1611081385000;
try {
  systemDateTime.setTime(time, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to set time. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in setting time`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set time. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.setTime

setTime(time : number) : Promise&lt;void&gt;

Sets the system time. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.Time

**Required permissions**: ohos.permission.SET_TIME

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| time   | number | Yes   | Target timestamp (ms), which must be greater than 0. |

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. resolve indicates that the system time is set successfully, and reject indicates that the system time fails to be set and returns error information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                                                                       |
| -------- |-------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                          |
| 202       | Permission verification failed. A non-system application calls a system API.                                |
| 204       | Access denied due to user access control policy. Possible causes: 1.The operation is restricted by the OS-account constraint. 2.The required privilege for the operation has not been granted.<br>Applicable version: 26.0.0+ |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Set the system time to 2021-01-20 02:36:25.
let time: number = 1611081385000;
try {
  systemDateTime.setTime(time).then(() => {
    console.info(`Succeeded in setting time.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to set time. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set time. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.setDate<sup>(deprecated)</sup>

setDate(date: Date, callback: AsyncCallback&lt;void&gt;): void

Sets the system date. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [systemDateTime.setTime](#systemdatetimesettime) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.Time

**Required permissions**: ohos.permission.SET_TIME

**Parameters**

| Name  | Type                     | Mandatory| Description         |
| -------- | ------------- | ---- |-------------|
| date     | Date                      | Yes   | Target date, which must be greater than 0. Error code 401 is returned if the value is less than or equal to 0. |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback invoked to return the result of setting the system date. If the setting is successful, err is undefined; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                                                                                                        |
| -------- |----------------------------------------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                                                           |
| 202       | Permission verification failed. A non-system application calls a system API.                                                                 |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let date = new Date();
try {
  systemDateTime.setDate(date, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to set date. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in setting date.`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set date. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.setDate<sup>(deprecated)</sup>

setDate(date: Date): Promise&lt;void&gt;

Sets the system date. This API uses a promise to return the result.

> **NOTE**
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [systemDateTime.setTime](#systemdatetimesettime) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.Time

**Required permissions**: ohos.permission.SET_TIME

**Parameters**

| Name| Type| Mandatory| Description      |
| ------ | ---- | ---- | ---------- |
| date   | Date | Yes   | Target date. The value must be greater than 0. If a value less than or equal to 0 is passed in, error code 401 is returned. |

**Return value**

| Type               | Description                |
| ------------------- | -------------------- |
| Promise&lt;void&gt; | Promise object that returns no value. resolve indicates that the system date is set successfully, and reject indicates that the system date fails to be set and returns error information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                                                                                                        |
| -------- |----------------------------------------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                                                           |
| 202       | Permission verification failed. A non-system application calls a system API.                                                                 |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let date = new Date(); 
try {
  systemDateTime.setDate(date).then(() => {
    console.info(`Succeeded in setting date.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to set date. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set date. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.setTimezone

setTimezone(timezone: string, callback: AsyncCallback&lt;void&gt;): void

Sets the system time zone. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.Time

**Required permissions**: ohos.permission.SET_TIME_ZONE

**Parameters**

| Name  | Type             | Mandatory| Description                 |
| -------- | ------------- | ---- | -------------------------- |
| timezone | string | Yes | System time zone. For details, see [Supported System Time Zones](#supported-system-time-zones). |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked to return the result of setting the system time zone. If the setting is successful, err is undefined; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                                                                       |
| -------- |-------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                          |
| 202       | Permission verification failed. A non-system application calls a system API.                                |
| 204       | Access denied due to user access control policy. Possible causes: 1.The operation is restricted by the OS-account constraint. 2.The required privilege for the operation has not been granted.<br>Applicable version: 26.0.0+ |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setTimezone('Asia/Shanghai', (error: BusinessError) => {
    if (error) {
      console.error(`Failed to set timezone. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in setting timezone.`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set timezone. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.setTimezone

setTimezone(timezone: string): Promise&lt;void&gt;

Sets the system time zone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.Time

**Required permissions**: ohos.permission.SET_TIME_ZONE

**Parameters**

| Name  | Type  | Mandatory| Description      |
| -------- | ------ | ---- | ---------- |
| timezone | string | Yes  | System time zone to set. For details, see [Supported System Time Zones](#supported-system-time-zones).|

**Return value**

| Type               | Description                |
| ------------------- | -------------------- |
| Promise&lt;void&gt; | Promise object that returns no value. resolve indicates that the system time zone is set successfully, and reject indicates that the system time zone fails to be set and returns error information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                                                                       |
| -------- |-------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                          |
| 202       | Permission verification failed. A non-system application calls a system API.                                |
| 204       | Access denied due to user access control policy. Possible causes: 1.The operation is restricted by the OS-account constraint. 2.The required privilege for the operation has not been granted.<br>Applicable version: 26.0.0+ |
| 401       | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setTimezone('Asia/Shanghai').then(() => {
    console.info(`Succeeded in setting timezone.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to set timezone. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set timezone. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.updateNtpTime<sup>14+</sup>

updateNtpTime(): Promise&lt;void&gt;

Updates the NTP time from the NTP server This API returns the result asynchronously. In this way, the NTP time is updated from the NTP server only once within one hour.

**Use scenario**: Used in scenarios where a system application needs to proactively calibrate the system time from a network time server, for example, when the device time is inaccurate or network time synchronization needs to be triggered manually.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.Time

**Return value**

| Type               | Description                |
| ------------------- | -------------------- |
| Promise&lt;void&gt; | Promise that returns no value. resolve indicates that the NTP time is updated from the NTP server successfully, and reject indicates that the NTP time fails to be updated and returns the error information. |

**Error codes**

For details about the error codes, see [Time and Time Zone Service Error Codes](./errorcode-time.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                                                                   |
|-------|-------------------------------------------------------------------------------------------------------------|
| 13000001    | Network connection error or OS error.                                                                 |
| 202   | Permission verification failed. A non-system application calls a system API.                                |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.updateNtpTime().then(() => {
    console.info(`Succeeded in updating ntp time.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to update ntp time. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to update ntp time. Code: ${error.code}, message: ${error.message}`);
}
```

## systemDateTime.getNtpTime<sup>14+</sup>

getNtpTime(): number

Obtains the real time calculated based on the last updated NTP time in synchronous mode. Before using this method, you must successfully call [updateNtpTime](#systemdatetimeupdatentptime14) to update the NTP time. Otherwise, error 13000002 is thrown.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.Time

**Return value**

| Type  | Description                            |
| ------ |--------------------------------|
| number | Unix epoch time (ms) calculated based on the last updated NTP time. |

**Error codes**

For details about the error codes, see [Time and Time Zone Service Error Codes](./errorcode-time.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                                                                   |
|-------|-------------------------------------------------------------------------------------------------------------|
| 13000002    | updateNtpTime() is not called successfully.                                                           |
| 202   | Permission verification failed. A non-system application calls a system API.                                |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let time: number = systemDateTime.getNtpTime();
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get ntp time. Code: ${error.code}, message: ${error.message}`);
}
```

## Supported System Time Zones

For the supported system time zones, see [I18n.SystemLocaleManager.getTimeZoneCityItemArray()](../apis-localization-kit/js-apis-i18n-sys.md#gettimezonecityitemarray10).


## systemDateTime.setAutoTimeStatus<sup>21+</sup>

setAutoTimeStatus(status: boolean): Promise&lt;void&gt;

Sets the status of the automatic time setting. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.Time

**Required permissions**: ohos.permission.SET_TIME

**Parameters**

| Name  | Type  | Mandatory| Description      |
| -------- | ------ | ---- | ---------- |
| status | boolean | Yes | Whether to set the automatic time setting switch status.<br>- true: enables the automatic time setting switch.<br>- false: disables the automatic time setting switch. |

**Return value**

| Type               | Description                |
| ------------------- | -------------------- |
| Promise&lt;void&gt; | Promise object that returns no value. resolve indicates that setting the automatic time switch state succeeds, and reject indicates that setting the automatic time switch state fails and returns error information. |

**Error codes**

For details about the error codes, see [Time and Time Zone Service Error Codes](./errorcode-time.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                                                                       |
| -------- |-------------------------------------------------------------------------------------------------------------|
| 201       | Permission denied.                                                                                          |
| 202       | Permission verification failed. A non-system application calls a system API.                                |
| 204       | Access denied due to user access control policy. Possible causes: 1.The operation is restricted by the OS-account constraint. 2.The required privilege for the operation has not been granted.<br>Applicable version: 26.0.0+ |
| 13000001  | Network connection error or OS error. Possible causes: 1.System memory is insufficient. 2.Calls the underlying system interface failed.|


**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setAutoTimeStatus(true).then(() => {
    console.info(`Succeeded in setting autotime.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to set autotime. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set autotime. Code: ${error.code}, message: ${error.message}`);
}
```