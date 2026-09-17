# getUkeyCertificateList

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## getUkeyCertificateList

```TypeScript
function getUkeyCertificateList(ukeyProvider: string, ukeyInfo: UkeyInfo): Promise<CMResult>
```

Obtains the list of USB Key credential . This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ukeyProvider | string | Yes | USB Key device provider |
| ukeyInfo | [UkeyInfo](arkts-devicecertificate-certificatemanager-ukeyinfo-i.md) | Yes | Attributes of a USB Key credential |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Promise used to return the operation result, that is, **credentialDetailList** in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.<br>The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. |
| [17500010](../errorcode-certManager.md#17500010-failed-to-access-the-usb-credential) | Indicates that access USB Key service failed. |
| [17500011](../errorcode-certManager.md#17500011-failed-to-validate-the-input-parameter) | Parameter verification failed.<br> Possible causes: the ukeyInfo parameter is invalid. For example, the parameter format is incorrect or the value range is invalid. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ukeyProvider: string = 'testProvider'; /* USB credential provider, which is omitted here. */
let ukeyInfo: certificateManager.UkeyInfo = { /* USB credential attributes. The value is omitted here. */
  certPurpose: certificateManager.CertificatePurpose.PURPOSE_DEFAULT,
}
try {
  certificateManager.getUkeyCertificateList(ukeyProvider, ukeyInfo).then((cmResult) => {
    let list: Array<certificateManager.Credential> = cmResult.credentialDetailList ?? [];
    console.info('Succeeded in getting USB key certificate list.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get USB key certificate list. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get USB key certificate list. Code: ${error.code}, message: ${error.message}`);
}
```
