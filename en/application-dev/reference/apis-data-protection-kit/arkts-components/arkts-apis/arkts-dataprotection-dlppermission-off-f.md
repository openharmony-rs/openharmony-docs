# off

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## off('openDLPFile')

```TypeScript
function off(type: 'openDLPFile', listener?: Callback<AccessedDLPFileInfo>): void
```

Unsubscribes from the DLP file open event. This API can be called only in non-DLP sandbox applications. After the API is successfully called, the application will no longer receive notifications for the DLP file open event.

This API is usually called to release resources when the page is destroyed or the subscription is no longer needed.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'openDLPFile' | Yes | Event type. It has a fixed value of **openDLPFile**, which indicates the DLP file open event. |
| listener | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccessedDLPFileInfo](arkts-dataprotection-dlppermission-accesseddlpfileinfo-i.md)&gt; | No | Callback for the DLP file open event. The application will not be notified when a DLP file is opened. By default, this parameter is left blank, which unregisters all callbacks for the file open event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100007](../errorcode-dlp.md#19100007-access-denied-for-a-dlp-sandbox-application) | No permission to call this API, which is available only for non-DLP sandbox applications. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |
