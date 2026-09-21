# installDLPSandbox (System API)

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## installDLPSandbox

```TypeScript
function installDLPSandbox(bundleName: string, access: DLPFileAccess, userId: number, uri: string): Promise<DLPSandboxInfo>
```

Installs a DLP sandbox application for an application. The DLP sandbox creates an independent running environment for protected DLP files, which is isolated from the original application process. This ensures that data is securely transferred within the authorized scope. The sandbox application inherits the functions of the original application but can access only authorized DLP files. This API uses a promise to return the result.

After calling **installDLPSandbox** to install a sandbox, the system must call [uninstallDLPSandbox](arkts-dataprotection-dlppermission-uninstalldlpsandbox-f-sys.md) to uninstall the sandbox after using it.

Before a DLP file management application opens a protected file, the system needs to install a DLP sandbox for the target application.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. The value contains 7 to 128 bytes. If the value is out of range, error code 401 is thrown. |
| access | [DLPFileAccess](arkts-dataprotection-dlppermission-dlpfileaccess-e.md) | Yes | Permission on the DLP file. The permissions on a DLP file determine the access scope of the file. |
| userId | number | Yes | Current user ID, which is the system account ID obtained by the account subsystem. The default super user ID is **100**.<br>The value range is [0, 2&lt;sup&gt;31&lt;/sup&gt;-1]. If the value is out of range, the excess part will be truncated. If the value of the passed parameter is less than 0, an error log is generated. |
| uri | string | Yes | URI of the DLP file. The value contains up to 4095 bytes. If the value is out of range, error code 401 is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DLPSandboxInfo](arkts-dataprotection-dlppermission-dlpsandboxinfo-i-sys.md)&gt; | Promise used to return the information about the sandbox application installed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.0.1 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
dlpPermission.installDLPSandbox('com.ohos.note', dlpPermission.DLPFileAccess.READ_ONLY, 100,
  uri).then((dlpSandboxInfo: dlpPermission.DLPSandboxInfo) => {
  console.info('dlpSandboxInfo: ', JSON.stringify(dlpSandboxInfo));
}).catch((error: BusinessError)=> {
  console.error(error.message);
}); // Install a DLP sandbox application.
```


<a id="installdlpsandbox-1"></a>

## installDLPSandbox

```TypeScript
function installDLPSandbox(bundleName: string, access: DLPFileAccess, userId: number, uri: string, callback: AsyncCallback<DLPSandboxInfo>): void
```

Installs a DLP sandbox application for an application. This API uses an asynchronous callback to return the result. After the API is called, the system creates a DLP sandbox for the application and returns the sandbox information.

After calling **installDLPSandbox** to install a sandbox, the system must call [uninstallDLPSandbox](arkts-dataprotection-dlppermission-uninstalldlpsandbox-f-sys.md) to uninstall the sandbox after using it.

Before a DLP file management application opens a protected file, the system needs to install a DLP sandbox for the target application.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. The value contains 7 to 128 bytes. If the value is out of range, error code 401 is thrown. |
| access | [DLPFileAccess](arkts-dataprotection-dlppermission-dlpfileaccess-e.md) | Yes | Permission on the DLP file. The permissions on a DLP file determine the access scope of the file. |
| userId | number | Yes | Current user ID, which is the system account ID obtained by the account subsystem. The default super user ID is **100**.<br>The value range is [0, 2&lt;sup&gt;31&lt;/sup&gt;-1]. If the value is out of range, the excess part will be truncated. If the value of the passed parameter is less than 0, an error log is generated. |
| uri | string | Yes | URI of the DLP file. The value contains up to 4095 bytes. If the value is out of range, error code 401 is thrown. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DLPSandboxInfo](arkts-dataprotection-dlppermission-dlpsandboxinfo-i-sys.md)&gt; | Yes | Callback used to return the result. If the DLP sandbox installation is successful, **err** is **undefined**, and **data** is the sandbox information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.0.1 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
dlpPermission.installDLPSandbox('com.ohos.note', dlpPermission.DLPFileAccess.READ_ONLY, 100, uri, (err, res) => {
  if (err) {
    console.error(`Failed to install DLPSandbox. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('res', JSON.stringify(res));
  }
}); // Install a DLP sandbox application.
```
