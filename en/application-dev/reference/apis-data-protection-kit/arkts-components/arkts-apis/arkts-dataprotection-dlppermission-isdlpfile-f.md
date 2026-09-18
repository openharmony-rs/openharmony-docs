# isDLPFile

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## isDLPFile

```TypeScript
function isDLPFile(fd: number): Promise<boolean>
```

Checks whether a file is a DLP file based on the FD. This API uses a promise to return the result.

During file processing, the system checks whether the file is a DLP file and then determines the subsequent processing policy. For example, whether to open the file in a DLP sandbox.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | FD of the file to be checked. The value range is [0, 2&lt;sup&gt;31&lt;/sup&gt;-1]. If the value of **fd** is less than 0, error code 19100001 is thrown. If the value of **fd** is greater than 2&lt;sup&gt;31&lt;/sup&gt;-1, the excess part will be truncated. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Returns `true` if fd is a DLP file; returns `false` otherwise. |

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
import { fileIo } from '@kit.CoreFileKit';

let uri = 'file://docs/storage/Users/currentUser/Documents/test.txt.dlp';
let file: number | undefined = undefined;
file = fileIo.openSync(uri).fd;
dlpPermission.isDLPFile(file).then((isDLPFile: boolean) => {
    console.info(JSON.stringify(isDLPFile));
}).catch((error: BusinessError) => {
    console.error(`Failed to check if file is DLP file. Code: ${error.code}, message: ${error.message}`);
}).finally(() => {
    if (file !== undefined) {
        fileIo.closeSync(file);
    }
});
```

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
let file: number | undefined = undefined;
file = fileIo.openSync(uri).fd;
dlpPermission.isDLPFile(file, (err, isDLPFile) => {
 if (err) {
    console.error(`Failed to check if file is DLP file. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('isDLPFile:', isDLPFile);
  }
  fileIo.closeSync(file);
});
```


## isDLPFile

```TypeScript
function isDLPFile(fd: number, callback: AsyncCallback<boolean>): void
```

Checks whether a file is a DLP file based on the FD. After the API is successfully called, a result is returned. The value **true** means the file is a DLP file; the value **false** means the opposite. This API uses an asynchronous callback to return the result.

During file processing, the system checks whether the file is a DLP file and then determines the subsequent processing policy. For example, whether to open the file in a DLP sandbox.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | FD of the file to be checked. The value range is [0, 2&lt;sup&gt;31&lt;/sup&gt;-1]. If the value of **fd** is less than 0, error code 19100001 is thrown. If the value of **fd** is greater than 2&lt;sup&gt;31&lt;/sup&gt;-1, the excess part will be truncated. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to receive the query result. The callback parameters include **err** and **res**. **err** is **undefined** when the query is successful; otherwise, **err** is an error object. If **true** is returned, **res** is a DLP file; if **false** is returned, **res** is not a DLP file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

See [isDLPFile](#isdlpfile)
