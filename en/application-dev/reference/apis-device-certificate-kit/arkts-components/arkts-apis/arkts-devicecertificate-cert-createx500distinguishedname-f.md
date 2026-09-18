# createX500DistinguishedName

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## createX500DistinguishedName

```TypeScript
function createX500DistinguishedName(nameStr: string): Promise<X500DistinguishedName>
```

Creates an **X500DistinguishedName** object with a name in the form of a string. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| nameStr | string | Yes | Name in a slash-separated format, each relative distinguished name is in the format of **attribute=value**. Common attributes include **CN** (common name), **O** (organization name), **OU** (organization unit), **C** (country/region), **ST** (province/state), and **L** (city/district). For example, **\/CN=example.com/O=Example/C=CN**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md)&gt; | Promise used to return the **X500DistinguishedName** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19020001](../errorcode-cert.md#19020001-memory-error) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-runtime-error) | Runtime error. Possible causes:<br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-failed-to-invoke-the-third-party-cryptographic-api) | Crypto operation error. |
| [19030002](../errorcode-cert.md#19030002-certificate-signature-verification-failed) | The certificate signature verification failed. |
| [19030003](../errorcode-cert.md#19030003-certificate-has-not-taken-effect) | The certificate has not taken effect. |
| [19030004](../errorcode-cert.md#19030004-certificate-expired) | The certificate has expired. |
| [19030005](../errorcode-cert.md#19030005-failed-to-obtain-the-certificate-issuer) | Failed to obtain the certificate issuer. |
| [19030006](../errorcode-cert.md#19030006-key-cannot-be-used-for-signing-a-certificate) | The key cannot be used for signing a certificate. |
| [19030007](../errorcode-cert.md#19030007-key-cannot-be-used-for-digital-signature) | The key cannot be used for a digital signature. |

**Examples**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Convert the string into a Uint8Array.
function stringToUint8Array(str: string): Uint8Array {
  let arr: Array<number> = [];
  for (let i = 0, j = str.length; i < j; i++) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

let nameStr = '/CN=John Doe/OU=IT Department/O=ACME Inc./L=San Francisco/ST=California/C=US/CN=ALN C/CN=XTS';
async function createX500DistinguishedName() {
  try {
    cert.createX500DistinguishedName(nameStr)
      .then((_data) => {
        console.info('createX500DistinguishedName result: success.');
      })
      .catch((err: BusinessError) => {
        console.error(`createX500DistinguishedName failed, errCode: ${err.code}, errMsg: ${err.message}`);
      });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX500DistinguishedName failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let nameDer =
  new Uint8Array([48, 41, 49, 11, 48, 9, 6, 3, 85, 4, 3, 12, 2, 67, 65, 49, 13, 48, 11, 6, 3, 85, 4, 10, 12, 4, 116,
    101, 115, 116, 49, 11, 48, 9, 6, 3, 85, 4, 6, 19, 2, 67, 78]);

async function createX500DistinguishedName() {
  try {
    cert.createX500DistinguishedName(nameDer)
      .then((_data) => {
        console.info('createX500DistinguishedName result: success.');
      })
      .catch((err: BusinessError) => {
        console.error(`createX500DistinguishedName failed, errCode: ${err.code}, errMsg: ${err.message}`);
      });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX500DistinguishedName failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```


## createX500DistinguishedName

```TypeScript
function createX500DistinguishedName(nameDer: Uint8Array): Promise<X500DistinguishedName>
```

Creates an **X500DistinguishedName** object with a name in DER format. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| nameDer | Uint8Array | Yes | X.500 Distinguished Name in DER format. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md)&gt; | Promise used to return the **X500DistinguishedName** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19020001](../errorcode-cert.md#19020001-memory-error) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-runtime-error) | Runtime error. Possible causes:<br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-failed-to-invoke-the-third-party-cryptographic-api) | Crypto operation error. |
| [19030002](../errorcode-cert.md#19030002-certificate-signature-verification-failed) | The certificate signature verification failed. |
| [19030003](../errorcode-cert.md#19030003-certificate-has-not-taken-effect) | The certificate has not taken effect. |
| [19030004](../errorcode-cert.md#19030004-certificate-expired) | The certificate has expired. |
| [19030005](../errorcode-cert.md#19030005-failed-to-obtain-the-certificate-issuer) | Failed to obtain the certificate issuer. |
| [19030006](../errorcode-cert.md#19030006-key-cannot-be-used-for-signing-a-certificate) | The key cannot be used for signing a certificate. |
| [19030007](../errorcode-cert.md#19030007-key-cannot-be-used-for-digital-signature) | The key cannot be used for a digital signature. |

**Examples**

See [createX500DistinguishedName](#createx500distinguishedname)
