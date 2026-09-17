# CertExtension

Provides APIs for operating on certificate extensions.

**Since:** 10

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## checkCA

```TypeScript
checkCA(): number
```

Checks whether the certificate is a CA certificate.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

**Return value:**

| Type | Description |
| --- | --- |
| number | If the key usage extension contains the keyCertSign bit and the CA field in the basic constraints is **true**, the certificate is a CA certificate. Returns **-1** if the certificate is not a CA certificate; returns the path length in the basic constraints otherwise. Returns **-2** if the certificate is a CA certificate but the path length is not specified in the basic constraints, which means the path length is not limited. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-memory-error) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-runtime-error) | Runtime error. Possible causes:<br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-failed-to-invoke-the-third-party-cryptographic-api) | Crypto operation error. |

**Examples**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Binary data of the certificate extension, which needs to be set to match your case.
let extData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);

let encodingBlob: cert.EncodingBlob = {
  data: extData,
  // Assign a value based on the encodingData format. Currently, only FORMAT_DER is supported.
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};
cert.createCertExtension(encodingBlob, (error, certExt) => {
  if (error) {
    console.error(`createCertExtension failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createCertExtension result: success.');
    try {
      let res = certExt.checkCA();
      console.info('res = ' + res);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`ext checkCA failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getEncoded

```TypeScript
getEncoded(): EncodingBlob
```

Obtains the serialized data of the certificate extensions.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

**Return value:**

| Type | Description |
| --- | --- |
| [EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md) | Serialized data obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-memory-error) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-runtime-error) | Runtime error. Possible causes:<br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-failed-to-invoke-the-third-party-cryptographic-api) | Crypto operation error. |

**Examples**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Binary data of the certificate extension, which needs to be set to match your case.
let extData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);

let encodingBlob: cert.EncodingBlob = {
  data: extData,
  // Assign a value based on the encodingData format. Currently, only FORMAT_DER is supported.
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};

cert.createCertExtension(encodingBlob, (error, certExt) => {
  if (error) {
    console.error(`createCertExtension failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createCertExtension result: success.');
    try {
      let extEncodedBlob = certExt.getEncoded();
      console.info('extEncodedBlob = ' + extEncodedBlob.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`ext getEncoded failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getEntry

```TypeScript
getEntry(valueType: ExtensionEntryType, oid: DataBlob): DataBlob
```

Obtains the value of a specific certificate extension entry by OID.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| valueType | [ExtensionEntryType](arkts-devicecertificate-cert-extensionentrytype-e.md) | Yes | Type of the information to obtain. |
| oid | [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | Yes | OID of the certificate extension to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | Certificate extension object information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19020001](../errorcode-cert.md#19020001-memory-error) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-runtime-error) | Runtime error. Possible causes:<br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-failed-to-invoke-the-third-party-cryptographic-api) | Crypto operation error. |

**Examples**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Binary data of the certificate extension, which needs to be set to match your case.
let extData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);

let encodingBlob: cert.EncodingBlob = {
  data: extData,
  // Assign a value based on the encodingData format. Currently, only FORMAT_DER is supported.
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};

cert.createCertExtension(encodingBlob, (error, certExt) => {
  if (error) {
    console.error(`createCertExtension failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createCertExtension result: success.');
    let oid = new Uint8Array([0x32, 0x2e, 0x35, 0x2e, 0x32, 0x39, 0x2e, 0x31, 0x35]);
    let oidBlob: cert.DataBlob = {
      data: oid
    };
    try {
      let entry = certExt.getEntry(cert.ExtensionEntryType.EXTENSION_ENTRY_TYPE_ENTRY, oidBlob);
      console.info('entry = ' + entry.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`ext getEntry failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getOidList

```TypeScript
getOidList(valueType: ExtensionOidType): DataArray
```

Obtains the OIDs of the certificate extensions.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| valueType | [ExtensionOidType](arkts-devicecertificate-cert-extensionoidtype-e.md) | Yes | Type of the OIDs to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | OIDs obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19020001](../errorcode-cert.md#19020001-memory-error) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-runtime-error) | Runtime error. Possible causes:<br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-failed-to-invoke-the-third-party-cryptographic-api) | Crypto operation error. |

**Examples**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Binary data of the certificate extension, which needs to be set to match your case.
let extData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);

let encodingBlob: cert.EncodingBlob = {
  data: extData,
  // Assign a value based on the encodingData format. Currently, only FORMAT_DER is supported.
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};

cert.createCertExtension(encodingBlob, (error, certExt) => {
  if (error) {
    console.error(`createCertExtension failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createCertExtension result: success.');
    try {
      let oidList = certExt.getOidList(cert.ExtensionOidType.EXTENSION_OID_TYPE_ALL);
      console.info('oidList = ' + oidList.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`ext getOidList failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## hasUnsupportedCriticalExtension

```TypeScript
hasUnsupportedCriticalExtension(): boolean
```

Checks whether there is a critical extension that is not supported.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if an unsupported critical extension is found; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-memory-error) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-runtime-error) | Runtime error. Possible causes:<br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-failed-to-invoke-the-third-party-cryptographic-api) | Crypto operation error. |

**Examples**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let encodingData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);
let encodingBlob: cert.EncodingBlob = {
  data: new Uint8Array(encodingData),
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};

cert.createCertExtension(encodingBlob).then((extensionObj) => {
  console.info('createCertExtension result: success.');
  const result = extensionObj.hasUnsupportedCriticalExtension();
  console.info('has unsupported critical extension result =' + result);
}).catch((err: BusinessError) => {
  console.error(`createCertExtension failed, errCode: ${err.code}, errMsg: ${err.message}`);
});
```
