# setAutoTimeStatus (System API)

## Modules to Import

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

## setAutoTimeStatus

```TypeScript
function setAutoTimeStatus(status: boolean): Promise<void>
```

Sets the status of the automatic time setting. This API uses a promise to return the result.

**Since:** 21

**Required permissions:** ohos.permission.SET_TIME

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| status | boolean | Yes | Whether to enable the automatic time setting.<br>- **true**: Enable the automatic time setting.<br>- **false**: Disable the automatic time setting. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [13000001](../errorcode-time.md#13000001-network-or-os-error) | Network connection error or OS error. Possible causes: 1. System memory is insufficient; 2. Calls the underlying system interface failed. |
| [204](../../errorcode-universal.md#204-access-denied-by-user-access-control-policy) | Access denied due to user access control policy. Possible causes: 1. The operation is restricted by the OS-account constraint. 2. The required privilege for the operation has not been granted.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setAutoTimeStatus(true).then(() => {
    console.info(`Succeeded in setting autotime.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to set autotime. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to set autotime. message: ${error.message}, code: ${error.code}`);
}
```
