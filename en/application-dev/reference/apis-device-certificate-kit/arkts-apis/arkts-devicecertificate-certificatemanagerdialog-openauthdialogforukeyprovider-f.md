# openAuthDialogForUkeyProvider

## Modules to Import

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## openAuthDialogForUkeyProvider

```TypeScript
function openAuthDialogForUkeyProvider(dialogInfo: UkeyAuthDialogInfo, ukeyAuthRequest: UkeyAuthRequest): Promise<void>
```

Opens the Ukey authentication dialog box of the USB Key credential. This API is invoked only by the Ukey driver application to implement the custom dialog box function in scenarios such as payment and certificate update. The Ukey authentication dialog box needs to be implemented by the Ukey driver application. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.CRYPTO_EXTENSION_REGISTER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dialogInfo | [UkeyAuthDialogInfo](arkts-devicecertificate-certificatemanagerdialog-ukeyauthdialoginfo-i.md) | Yes | Information about the Ukey authentication dialog box to be opened. |
| ukeyAuthRequest | [UkeyAuthRequest](arkts-devicecertificate-certificatemanagerdialog-ukeyauthrequest-i.md) | Yes | Authentication request information of the USB Key credential. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the certificate management application hap is not preinstalled in the system. |
| [29700001](../errorcode-certManagerDialog.md#29700001-internal-error) | The certificate manager service processing failed. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| [29700002](../errorcode-certManagerDialog.md#29700002-operation-canceled) | The user cancels the authentication operation. |
| [29700003](../errorcode-certManagerDialog.md#29700003-failed-to-install-the-certificate) | The authentication operation failed, such as: The USB key certificate does not exist. The USB key status is abnormal, Please ask the user to check the status of the Ukey. |
| [29700005](../errorcode-certManagerDialog.md#29700005-non-secure-operation) | The operation does not comply with the device security policy. Only the PC/2in1 device can open the dialog box of the UkeyAuthExtensionAbility type. |
| [29700006](../errorcode-certManagerDialog.md#29700006-failed-to-validate-the-input-parameter) | Indicates that the input parameters validation failed. For example, the parameter format is incorrect or the value range is invalid. |
| 29700009 | The operation in the Ukey authentication dialog box timed out. |
| 29700010 | The Ukey authentication dialog box cannot be opened concurrently. Please try again later. |
