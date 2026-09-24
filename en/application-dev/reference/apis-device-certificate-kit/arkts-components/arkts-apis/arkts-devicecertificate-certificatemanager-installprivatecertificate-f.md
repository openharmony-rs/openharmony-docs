# installPrivateCertificate

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## installPrivateCertificate

```TypeScript
function installPrivateCertificate(
    keystore: Uint8Array,
    keystorePwd: string,
    certAlias: string,
    callback: AsyncCallback<CMResult>
  ): void
```

Installs a private credential. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keystore | Uint8Array | Yes | Keystore file with a key pair and certificate. The value contains up to 20480 bytes. |
| keystorePwd | string | Yes | Password of the keystore file. The password cannot exceed 32 bytes. |
| certAlias | string | Yes | Credential alias. Currently, the alias can contain only digits, letters, and underscores (_) and should not exceed 32 bytes. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is **uri** in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500003](../errorcode-certManager.md#17500003-invalid-certificate-or-credential) | The keystore is in an invalid format or the keystore password is incorrect. |
| [17500004](../errorcode-certManager.md#17500004-the-number-of-certificates-or-credentials-reaches-the-limit) | The number of certificates or credentials reaches the maximum allowed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

/* The credential data to be installed must be assigned by the service. The data in this example is not the real credential data. */
let keystore: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let keystorePwd: string = "123456";
try {
  certificateManager.installPrivateCertificate(keystore, keystorePwd, "test", (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to install private certificate. Code: ${err.code}, message: ${err.message}`);
    } else {
      let uri: string = cmResult?.uri ?? '';
      console.info('Succeeded in installing private certificate.');
    }
  });
} catch (error) {
  console.error(`Failed to install private certificate. Code: ${error.code}, message: ${error.message}`);
}
```


<a id="installprivatecertificate-1"></a>

## installPrivateCertificate

```TypeScript
function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string): Promise<CMResult>
```

Installs a private credential. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keystore | Uint8Array | Yes | Keystore file with a key pair and certificate. The value contains up to 20480 bytes. |
| keystorePwd | string | Yes | Password of the keystore file. The password cannot exceed 32 bytes. |
| certAlias | string | Yes | Credential alias. Currently, the alias can contain only digits, letters, and underscores (_) and should not exceed 32 bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Promise used to return the operation result, that is, **uri** in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500003](../errorcode-certManager.md#17500003-invalid-certificate-or-credential) | The keystore is in an invalid format or the keystore password is incorrect. |
| [17500004](../errorcode-certManager.md#17500004-the-number-of-certificates-or-credentials-reaches-the-limit) | The number of certificates or credentials reaches the maximum allowed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* The credential data to be installed must be assigned by the service. The data in this example is not the real credential data. */
let keystore: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let keystorePwd: string = "123456";
try {
  certificateManager.installPrivateCertificate(keystore, keystorePwd, 'test').then((cmResult) => {
    let uri: string = cmResult?.uri ?? '';
    console.info('Succeeded in installing private certificate.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to install private certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to install private certificate. Code: ${error.code}, message: ${error.message}`);
}
```


<a id="installprivatecertificate-2"></a>

## installPrivateCertificate

```TypeScript
function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, level: AuthStorageLevel): Promise<CMResult>
```

Installs a private credential and specifies its storage level. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keystore | Uint8Array | Yes | Keystore file with a key pair and certificate. The value contains up to 20480 bytes. |
| keystorePwd | string | Yes | Password of the keystore file.<br>The value contains up to 32 bytes. |
| certAlias | string | Yes | Alias of the credential entered by the user. Only digits, letters, and underscores (_) are supported.<br>The value should contain up to 32 bytes. |
| level | [AuthStorageLevel](arkts-devicecertificate-certificatemanager-authstoragelevel-e.md) | Yes | Credential storage level. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Promise used to return the operation result, that is, **uri** in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500003](../errorcode-certManager.md#17500003-invalid-certificate-or-credential) | The keystore is in an invalid format or the keystore password is incorrect. |
| [17500004](../errorcode-certManager.md#17500004-the-number-of-certificates-or-credentials-reaches-the-limit) | The number of certificates or credentials reaches the maximum allowed. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* The data of the credential to be installed must be assigned based on the service. The data in this example is not the real credential data. */
let keystore: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let keystorePwd: string = "123456";
try {
  /* The credential can be used after the device is unlocked for the first time. */
  let level = certificateManager.AuthStorageLevel.EL2;
  certificateManager.installPrivateCertificate(keystore, keystorePwd, 'test', level).then((cmResult) => {
    let uri: string = cmResult.uri ?? '';
    console.info('Succeeded in installing private certificate.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to install private certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to install private certificate. Code: ${error.code}, message: ${error.message}`);
}
```
