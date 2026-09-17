# isInSandbox

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## isInSandbox

```TypeScript
function isInSandbox(): Promise<boolean>
```

Checks whether this application is running in a DLP sandbox environment. This API uses a promise to return the result.

This API is used to determine whether the current application is running in a DLP sandbox environment. If it is, the system can perform operations or call APIs for sandbox applications.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the application is running in a sandbox; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isInSandbox().then((isInSandbox) => { // Check whether the application is running in a sandbox.
  console.info('isInSandbox', isInSandbox);
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isInSandbox((err, isInSandbox) => {
  if (err) {
    console.error(`Failed to check sandbox status. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('isInSandbox: ', JSON.stringify(isInSandbox));
  }
}); // Whether the application is running in a sandbox.
```


## isInSandbox

```TypeScript
function isInSandbox(callback: AsyncCallback<boolean>): void
```

Checks whether this application is running in a DLP sandbox environment. This API uses an asynchronous callback to return the result.

This API is used to determine whether the current application is running in a DLP sandbox environment. If it is, the system can perform operations or call APIs for sandbox applications.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. The value **true** means the application is running in a sandbox; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

See [isInSandbox](#isinsandbox)
