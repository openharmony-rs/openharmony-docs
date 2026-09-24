# finish

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## finish

```TypeScript
function finish(handle: Uint8Array, callback: AsyncCallback<CMResult>): void
```

Finishes the signing operation. This is the last step in the signature process. The init and update interfaces need to be invoked first. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | Uint8Array | Yes | Handle of initialization. You need to invoke the init method to obtain the handle. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the signature, that is, **outData** of the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

/* cmHandle is the value returned by init(). The value here is only an example. */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.finish(cmHandle, (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to finish. Code: ${err.code}, message: ${err.message}`);
    } else {
      if (cmResult?.outData != undefined) {
        let signRes = cmResult?.outData;
        console.info('Succeeded in finishing.');
      } else {
        console.info('The result of finishing is undefined.');
      }
    }
  });
} catch(error) {
  console.error(`Failed to finish. Code: ${error.code}, message: ${error.message}`);
}
```


<a id="finish-1"></a>

## finish

```TypeScript
function finish(handle: Uint8Array, signature: Uint8Array, callback: AsyncCallback<CMResult>): void
```

Finishes the signature verification operation. This is the last step in the signature verification process. The init and update interfaces need to be invoked first. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | Uint8Array | Yes | Handle of initialization. You need to invoke the init method to obtain the handle. |
| signature | Uint8Array | Yes | Data to sign or verify. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

/* cmHandle is the value returned by init(). The value here is only an example. */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
let signRes: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.finish(cmHandle, signRes, (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to finish. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in finishing.');
    }
  });
} catch(error) {
  console.error(`Failed to finish. Code: ${error.code}, message: ${error.message}`);
}
```


<a id="finish-2"></a>

## finish

```TypeScript
function finish(handle: Uint8Array, signature?: Uint8Array): Promise<CMResult>
```

Finishes the signing or signature verification operation. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | Uint8Array | Yes | Handle of initialization. You need to invoke the init method to obtain the handle. |
| signature | Uint8Array | No | Signature data used for signature verification. This parameter does not need to be specified for signature operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Promise used to return the signature of a signing operation, that is, **outData** in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. For a signature verification operation, the promise returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* cmHandle is the value returned by init(). The value here is only an example. */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  /* Finish the signing operation. */
  certificateManager.finish(cmHandle).then((cmResult) => {
    if (cmResult?.outData != undefined) {
      let signRes1 = cmResult?.outData;
      console.info('Succeeded in finishing signature.');
    } else {
      console.info('The result of signature is undefined.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to finish signature. Code: ${err.code}, message: ${err.message}`);
  })

  /* Signature generated. */
  let signRes: Uint8Array = new Uint8Array([
    0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
  ]);
  /* Finish the signature verification operation. */
  certificateManager.finish(cmHandle, signRes).then((cmResult) => {
    console.info('Succeeded in finishing verification.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to finish verification. Code: ${err.code}, message: ${err.message}`);
  })
} catch(error) {
  console.error(`Failed to finish. Code: ${error.code}, message: ${error.message}`);
}
```
