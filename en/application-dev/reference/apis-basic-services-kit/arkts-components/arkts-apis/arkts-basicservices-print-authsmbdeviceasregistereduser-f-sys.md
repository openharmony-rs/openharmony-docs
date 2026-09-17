# authSmbDeviceAsRegisteredUser (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## authSmbDeviceAsRegisteredUser

```TypeScript
function authSmbDeviceAsRegisteredUser(host: SharedHost, username: string, password: string): Promise<PrinterInformation[]>
```

Authenticate SMB device as registered user and get available printers.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| host | [SharedHost](arkts-basicservices-print-sharedhost-i.md) | Yes | The SMB host to authenticate.<br>The SMB host to authenticate. |
| username | string | Yes | The username for authentication.<br>User name used for authentication. |
| password | string | Yes | The password for authentication.<br>Password used for authentication. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PrinterInformation](arkts-basicservices-print-printerinformation-i.md)[]&gt; | Promise that resolves with the list of available printers. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
| 13100012 | SMB account is locked due to multiple failed login attempts. |
| 13100013 | SMB connection failed (network error, host unreachable, or port blocked). |
| 13100014 | Invalid login account or password. |
