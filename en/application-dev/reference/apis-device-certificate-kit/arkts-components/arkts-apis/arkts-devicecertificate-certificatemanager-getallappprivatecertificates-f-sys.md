# getAllAppPrivateCertificates (System API)

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## getAllAppPrivateCertificates

```TypeScript
function getAllAppPrivateCertificates(callback: AsyncCallback<CMResult>): void
```

Obtains all private credentials. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability:** SystemCapability.Security.CertificateManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Yes | Callback used to return the result. If all private credentials are obtained, **err** is **null**, and **data** is the **credentialList** attribute in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

try {
  certificateManager.getAllAppPrivateCertificates((err, cmResult) => {
    if (err != null) {
      console.error(`Failed to get all app private certificates. Code: ${err.code}, message: ${err.message}`);
    } else {
      if (cmResult === undefined) { // If the number of private credentials is 0, return undefined in cmResult.
        console.info('The count of the app private certificates is 0.');
      } else if (cmResult.credentialList == undefined) {
        console.info('The result of getting all app private certificates is undefined.');
      } else {
        let list = cmResult.credentialList;
        console.info('Succeeded in getting all app private certificates.');
      }
    }
  });
} catch (error) {
  console.error(`Failed to get all app private certificates. Code: ${error.code}, message: ${error.message}`);
}
```


<a id="getallappprivatecertificates-1"></a>

## getAllAppPrivateCertificates

```TypeScript
function getAllAppPrivateCertificates(): Promise<CMResult>
```

Obtains all private credentials. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability:** SystemCapability.Security.CertificateManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Promise used to return the result, which is the value of **credentialList** in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  certificateManager.getAllAppPrivateCertificates().then((cmResult) => {
    if (cmResult === undefined) { // If the number of private credentials is 0, return undefined in cmResult.
      console.info('The count of the app private certificates is 0.');
    } else if (cmResult.credentialList == undefined) {
      console.info('The result of getting all app private certificates is undefined.');
    } else {
      let list = cmResult.credentialList;
      console.info('Succeeded in getting all app private certificates.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get all app private certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get all app private certificates. Code: ${error.code}, message: ${error.message}`);
}
```
