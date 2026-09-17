# cancelRetentionState

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## cancelRetentionState

```TypeScript
function cancelRetentionState(docUris: Array<string>): Promise<void>
```

Cancels the sandbox retention state, that is, allows the sandbox application to be automatically uninstalled when the DLP file is closed. This API uses a promise to return the result.

This API is used to cancel the retention state for sandbox application and restore the default behavior to release system resources. It is applicable to scenarios where the DLP file is no longer frequently accessed.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| docUris | Array&lt;string&gt; | Yes | URIs of the files to be canceled with the retention state. The length of the array is not limited. Each string contains a maximum of 4095 bytes. If the string is out of range, error code 401 is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
dlpPermission.cancelRetentionState([uri]).then(() => { // Cancel the retention state for a sandbox application.
  console.info('success!');
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
dlpPermission.cancelRetentionState([uri], (err, res) => {
  if (err) {
    console.error(`Failed to cancel retention state. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('cancelRetentionState success');
  }
}); // Cancel the sandbox retention state.
```


## cancelRetentionState

```TypeScript
function cancelRetentionState(docUris: Array<string>, callback: AsyncCallback<void>): void
```

Cancels the sandbox retention state, that is, allows the sandbox application to be automatically uninstalled when the DLP file is closed. This API uses an asynchronous callback to return the result.

This API is used to cancel the retention state for sandbox application and restore the default behavior to release system resources. It is applicable to scenarios where the DLP file is no longer frequently accessed.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| docUris | Array&lt;string&gt; | Yes | URIs of the files to be canceled with the retention state. The length of the array is not limited. Each string contains a maximum of 4095 bytes. If the string is out of range, error code 401 is thrown. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the cancellation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

See [cancelRetentionState](#cancelretentionstate)
