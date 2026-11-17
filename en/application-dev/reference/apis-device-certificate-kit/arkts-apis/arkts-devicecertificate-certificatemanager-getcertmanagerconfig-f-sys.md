# getCertManagerConfig (System API)

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## getCertManagerConfig

```TypeScript
function getCertManagerConfig(configNames: Array<string>) : Promise<Array<ConfigItem>>
```

Queries the certificate management system configuration information.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**Model restriction:** This API can be used only in the stage model.

<!--Device-certificateManager-function getCertManagerConfig(configNames: Array<string>) : Promise<Array<ConfigItem>>--><!--Device-certificateManager-function getCertManagerConfig(configNames: Array<string>) : Promise<Array<ConfigItem>>-End-->

**System capability:** SystemCapability.Security.CertificateManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configNames | Array&lt;string&gt; | Yes | Certificate management configuration item names. <br>The maximum length is 16 bytes and cannot be empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ConfigItem](arkts-devicecertificate-certificatemanager-configitem-i-sys.md)&gt;&gt; | Promise used to return the config data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. <br> The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [17500011](../errorcode-certManager.md#17500011-failed-to-validate-the-input-parameter) | The input parameters validation failed. <br> Possible causes: The length of configNames exceeds the limit, or the array is empty, or the array element value is invalid. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed; <br>2. Memory operation error; 3. File operation error. Please try again. |
