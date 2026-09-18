# importUkeyCertificate

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## importUkeyCertificate

```TypeScript
function importUkeyCertificate(keyUri: string, cert: Uint8Array, ukeyInfo: UkeyInfo): Promise<void>
```

Import the certificate to the USB Key.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyUri | string | Yes | Indicates the USB Key credentials URI. <br>The maximum length is 256 and cannot be empty. <br> The keyUri parameter identifies a certificate entity, which can be obtained <br>by calling the [getUkeyCertificateList](arkts-devicecertificate-certificatemanager-getukeycertificatelist-f.md) interface. |
| cert | Uint8Array | Yes | Indicates the certificate data to be imported.<br>The maximum length is 10240 and cannot be empty. <br>The certificate data format complies with the Smart Key Framework (SKF) specifications. |
| ukeyInfo | [UkeyInfo](arkts-devicecertificate-certificatemanager-ukeyinfo-i.md) | Yes | Indicates USB Key certificate attribute information.<br>UkeyInfo.CertificatePurpose can only be set to PURPOSE_SIGN, PURPOSE_ENCRYPT or PURPOSE_DEFAULT. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-certificate-not-exist) | The certificate identified by keyUri does not exist |
| [17500010](../errorcode-certManager.md#17500010-failed-to-access-the-usb-credential) | Indicates that access USB Key service failed. |
| [17500011](../errorcode-certManager.md#17500011-failed-to-validate-the-input-parameter) | Indicates that the input parameters validation failed. For example, the parameter format is incorrect or the value range is invalid. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* keyUri and cert must be assigned based on the service. The data in this example is for reference only. */
let keyUri: string = 'test'; /* URI of the USB key certificate, which can be obtained using the getUkeyCertificateList API. */
let certData: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let ukeyInfo: certificateManager.UkeyInfo = {
  certPurpose: certificateManager.CertificatePurpose.PURPOSE_SIGN,
};
try {
  certificateManager.importUkeyCertificate(keyUri, certData, ukeyInfo).then(() => {
    console.info('Succeeded in importing USB key certificate.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to import USB key certificate. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  console.error(`Failed to import USB key certificate. Code: ${error.code}, message: ${error.message}`);
}
```
