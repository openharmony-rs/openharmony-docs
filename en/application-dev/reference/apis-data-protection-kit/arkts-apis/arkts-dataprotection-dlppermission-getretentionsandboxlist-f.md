# getRetentionSandboxList

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## getRetentionSandboxList

```TypeScript
function getRetentionSandboxList(bundleName?: string): Promise<Array<RetentionSandboxInfo>>
```

Obtains the sandbox applications in the retention state of an application. This API can be called only in non-DLP sandbox applications. This API uses a promise to return the result.

This API is used to query the sandbox retention information of a specified application, so that the sandbox environment in the retention state can be checked or managed.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | No | Bundle name of the application, which is used to query the sandbox retention information of the application. This parameter is required when you need to query the sandbox retention information of another application. It is optional when you need to query the sandbox retention information of the current application. The value contains 7 to 128 bytes. If the value is out of range, error code 401 is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[RetentionSandboxInfo](arkts-dataprotection-dlppermission-retentionsandboxinfo-i.md)&gt;&gt; | Promise used to return the sandbox retention information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.0.1 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100007](../errorcode-dlp.md#19100007-access-denied-for-a-dlp-sandbox-application) | No permission to call this API, which is available only for non-DLP sandbox applications. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getRetentionSandboxList().then((sandboxList) => { // Obtain the sandbox retention information.
  console.info('sandboxList', JSON.stringify(sandboxList));
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```


<a id="getretentionsandboxlist-1"></a>

## getRetentionSandboxList

```TypeScript
function getRetentionSandboxList(bundleName: string, callback: AsyncCallback<Array<RetentionSandboxInfo>>): void
```

Obtains the sandbox applications in the retention state of an application. This API uses an asynchronous callback to return the result.

This API is used to query the sandbox retention information of a specified application, so that the sandbox environment in the retention state can be checked or managed.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application, which is used to query the sandbox retention information of the application. This parameter is required when you need to query the sandbox retention information of another application. It is optional when you need to query the sandbox retention information of the current application. The value contains 7 to 128 bytes. If the value is out of range, error code 401 is thrown. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[RetentionSandboxInfo](arkts-dataprotection-dlppermission-retentionsandboxinfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.0.1 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100007](../errorcode-dlp.md#19100007-access-denied-for-a-dlp-sandbox-application) | No permission to call this API, which is available only for non-DLP sandbox applications. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getRetentionSandboxList('bundleName', (err, sandboxList) => {
  if (err) {
    console.error(`Failed to get retention sandbox list. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('sandboxList', JSON.stringify(sandboxList));
  }
}); // Obtain the sandbox retention information.
```


<a id="getretentionsandboxlist-2"></a>

## getRetentionSandboxList

```TypeScript
function getRetentionSandboxList(callback: AsyncCallback<Array<RetentionSandboxInfo>>): void
```

Obtains the sandbox applications in the retention state of an application. This API uses an asynchronous callback to return the result.

This API is used to query the sandbox retention information of the current application, so that the sandbox environment in the retention state can be checked or managed. This API can be called only in non-DLP sandbox applications.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[RetentionSandboxInfo](arkts-dataprotection-dlppermission-retentionsandboxinfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.0.1 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100007](../errorcode-dlp.md#19100007-access-denied-for-a-dlp-sandbox-application) | No permission to call this API, which is available only for non-DLP sandbox applications. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getRetentionSandboxList((err, retentionSandboxList) => {
  if (err) {
    console.error(`Failed to get retention sandbox list. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('retentionSandboxList', JSON.stringify(retentionSandboxList));
  }
}); // Obtain the sandbox retention information.
```
