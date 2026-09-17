# openUkeyAuthDialog

## Modules to Import

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## openUkeyAuthDialog

```TypeScript
function openUkeyAuthDialog(context: common.Context, ukeyAuthRequest: UkeyAuthRequest): Promise<void>
```

Opens the PIN authentication dialog box of the USB Key credential. On the displayed page, the user can enter the PIN to authorize the USB credential. After the call is successful, the USB key credential will be unlocked. The app can use the credential to perform operations such as signing and encryption. This API uses a promise to return the result.

**Since:** 22

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [common.Context](../../apis-ability-kit/arkts-apis/arkts-ability-common-context-t.md) | Yes | Context of the application. |
| ukeyAuthRequest | [UkeyAuthRequest](arkts-devicecertificate-certificatemanagerdialog-ukeyauthrequest-i.md) | Yes | Authentication request information of the USB Key credential |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [29700006](../errorcode-certManagerDialog.md#29700006-failed-to-validate-the-input-parameter) | Indicates that the input parameters validation failed. For example, the parameter format is incorrect or the value range is invalid. |
| [29700001](../errorcode-certManagerDialog.md#29700001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [29700002](../errorcode-certManagerDialog.md#29700002-operation-canceled) | The user cancels the authentication operation. |
| [29700003](../errorcode-certManagerDialog.md#29700003-failed-to-install-the-certificate) | The authentication operation failed, such as the USB key certificate does not exist, the USB key status is abnormal. |

**Examples**

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context is application context information, which is obtained by the caller. The context here is only an example. */
let context: common.Context = new UIContext().getHostContext() as common.Context;
/* keyUri is the unique identifier of the credential. The invoker obtains the value by itself. The value here is only an example. */
let keyUri: string = "test"
let ukeyAuthRequest: certificateManagerDialog.UkeyAuthRequest = { keyUri: keyUri }
try {
  certificateManagerDialog.openUkeyAuthDialog(context, ukeyAuthRequest).then(() => {
    console.info(`Succeeded in opening ukey authorization dialog`)
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to open ukey authorization dialog. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to open ukey authorization dialog. Code: ${error.code}, message: ${error.message}`);
}
```
