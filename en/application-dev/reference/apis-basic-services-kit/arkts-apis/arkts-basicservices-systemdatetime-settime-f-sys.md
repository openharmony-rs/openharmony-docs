# setTime (System API)

## Modules to Import

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

## setTime

```TypeScript
function setTime(time: number, callback: AsyncCallback<void>): void
```

Sets the system time. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.SET_TIME

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| time | number | Yes | Timestamp to set, in milliseconds, and must be greater than 0. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameter types. |
| [204](../../errorcode-universal.md#204-access-denied-by-user-access-control-policy) | Access denied due to user access control policy. Possible causes: 1. The operation is restricted by the OS-account constraint. 2. The required privilege for the operation has not been granted.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Set the system time to 2021-01-20 02:36:25.
let time: number = 1611081385000;
try {
  systemDateTime.setTime(time, (error: BusinessError) => {
    if (error) {
      console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in setting time`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
}
```


<a id="settime-1"></a>

## setTime

```TypeScript
function setTime(time: number): Promise<void>
```

Sets the system time. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.SET_TIME

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| time | number | Yes | Timestamp to set, in milliseconds, and must be greater than 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameter types. |
| [204](../../errorcode-universal.md#204-access-denied-by-user-access-control-policy) | Access denied due to user access control policy. Possible causes: 1. The operation is restricted by the OS-account constraint. 2. The required privilege for the operation has not been granted.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Set the system time to 2021-01-20 02:36:25.
let time: number = 1611081385000;
try {
  systemDateTime.setTime(time).then(() => {
    console.info(`Succeeded in setting time.`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set time. message: ${error.message}, code: ${error.code}`);
}
```
