# CertChainValidator

Provides APIs for certificate chain validator operations.

**Since:** 9

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## validate

```TypeScript
validate(certChain: CertChainData, callback: AsyncCallback<void>): void
```

Validates an X.509 certificate chain. This API uses an asynchronous callback to return the result.

<br>Because the system time on the device is untrusted, the certificate chain validator does not verify the certificate validity period. To check the validity period of a certificate, use the [checkValidityWithDate()](arkts-devicecertificate-cert-x509cert-i.md#checkvaliditywithdate) API of the **X509Cert** class. For details about certificate specifications, see [Certificate Specifications](../../../security/DeviceCertificateKit/certificate-framework-overview.md#certificate-specifications).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| certChain | [CertChainData](arkts-devicecertificate-cert-certchaindata-i.md) | Yes | Serialized X.509 certificate chain data. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

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

// Binary data of the certificate chain.
let certPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIDTjCCAjagAwIBAgIBBDANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDQwMVoXDTM0MDMxNzAyMDQwMVowEjEQMA4GA1UEAwwH\n' +
  'ZGV2aWNlMjCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAMIXL3e7UE/c\n' +
  'Z1dPVgRZ5L8gsQ/azuYVBvoFf7o8ksYrL7G1+qZIJjVRqZkuTirLW4GicbkIkPNW\n' +
  'eix5cDhkjkC+q5SBCOrSSTTlvX3xcOY1gMlA5MgeBfGixFusq4d5VPF2KceZ20/a\n' +
  'ygwGD0Uv0X81OERyPom/dYdJUvfaD9ifPFJ1fKIj/cPFG3yJK/ojpEfndZNdESQL\n' +
  'TkoDekilg2UGOLtY6fb9Ns37ncuIj33gCS/R9m1tgtmqCTcgOQ4hwKhjVF3InmPO\n' +
  '2BbWKvD1RUX+rHC2a2HHDQILOOtDTy8dHvE+qZlK0efrpRgoFEERJAGPi1GDGWiA\n' +
  '7UX1c4MCxIECAwEAAaOBrjCBqzAJBgNVHRMEAjAAMB0GA1UdDgQWBBQbkAcMT7ND\n' +
  'fGp3VPFzYHppZ1zxLTAfBgNVHSMEGDAWgBR0W/koCbvDtFGHUQZLM3j6HKsW2DAd\n' +
  'BgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwCwYDVR0PBAQDAgeAMDIGCCsG\n' +
  'AQUFBwEBBCYwJDAiBggrBgEFBQcwAYYWaHR0cHM6Ly8xMjcuMC4wLjE6OTk5OTAN\n' +
  'BgkqhkiG9w0BAQsFAAOCAQEAF1OTzTmbklFOdZCxrF3zg9owUPJR5RB+PbuBlUfI\n' +
  '8tkGXkMltQ8PN1dv6Cq+d8BluiJdWEzqVoJa/e5SHHJyYQSOhlurRG0GBXllVQ1I\n' +
  'n1PFaI40+9X2X6wrEcdC5nbzogR1jSiksCiTcARMddj0Xrp5FMrFaaGY8M/xqzdW\n' +
  'LTDl4nfbuxtA71cIjnE4kOcaemly9/S2wYWdPktsPxQPY1nPUOeJFI7o0sH3rK0c\n' +
  'JSqtgAG8vnjK+jbx9RpkgqCsXgUbIahL573VTgxrNrsRjCuVal7XVxl/xOKXr6Er\n' +
  'Gpc+OCrXbHNZkUQE5fZH3yL2tXd7EASEb6J3aEWHfF8YBA==\n' +
  '-----END CERTIFICATE-----';

let caPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIC/zCCAeegAwIBAgIBATANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDIyNFoXDTM0MDMxNzAyMDIyNFowEjEQMA4GA1UEAwwH\n' +
  'Um9vdCBDQTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALxI5SDvRfKU\n' +
  '6XaTeyh2LHlUK0rVSeYfXkYf5Mc3Pgucg+ewzQjxkACMx5NYaW1zfGDNPG1i5IZl\n' +
  'cPeWNz1Tm2g6wTd+LyNoNOOmwfLV8pLXSfAukgNrBREf3BzVrbu7hvPd2MmLH23H\n' +
  'OBM9uDPTIqu3n2CDN2EzwULjaSk2g+jvhVKsDLInu5uKPmZBFhs1FWKgcnVnlbi1\n' +
  'AyAx4efheits6EO70oV6UufCEtS1VsBXQHZRAG4ogshWldRBVNxkU6yHAfg0mM/5\n' +
  'EhrZsfh51fWqlrhNWrInjgNV3xIt5ebTIgKZWUlSVHEA/UqDoGfY+CsAJdteZWOW\n' +
  'KjsrC/DK2O0CAwEAAaNgMF4wHQYDVR0OBBYEFHRb+SgJu8O0UYdRBkszePocqxbY\n' +
  'MB8GA1UdIwQYMBaAFHRb+SgJu8O0UYdRBkszePocqxbYMA8GA1UdEwEB/wQFMAMB\n' +
  'Af8wCwYDVR0PBAQDAgEGMA0GCSqGSIb3DQEBCwUAA4IBAQAKOT1ObfQNMN2wdfHq\n' +
  'PQgFDDp6rBMbZe70LswPirSXljo4S/vfbG+gBoWCdu/SfsV+lyP75kg1wX0IQvzW\n' +
  'xYNh864dgqPmGd0v8TIfM0UT0PpnowUyBHQ+E7LNYIOh/kjHbl3oERdEFA2PUyE9\n' +
  'j3GLdg8oe/LqhEQCSAlH+v2RQgBZ9eVN+mSdUxwywm9U3acb0uqVkGiWK/ywumpg\n' +
  'AmIZLMJtMVvg8uDkfy16Z4lChTEdNaJVUqPczUNk2kHXIF4we4be9HoOuTVz/SD/\n' +
  'IsOhXn/BjS3jnhyS9fxo+opJf9zVTWI02Hlh1WVVtH/m3nIZblyAJhcjCHA2wZSz\n' +
  'sSus\n' +
  '-----END CERTIFICATE-----';

let certPemData = stringToUint8Array(certPem);
let caPemData = stringToUint8Array(caPem);

let certPemDataLenData = new Uint8Array(new Uint16Array([certPemData.length]).buffer);
let caPemDataLenData = new Uint8Array(new Uint16Array([caPemData.length]).buffer);

let certChainBuff =
  new Uint8Array(certPemDataLenData.length + certPemData.length + caPemDataLenData.length + caPemData.length);
certChainBuff.set(certPemDataLenData);
certChainBuff.set(certPemData, certPemDataLenData.length);
certChainBuff.set(caPemDataLenData, certPemDataLenData.length + certPemData.length);
certChainBuff.set(caPemData, certPemDataLenData.length + certPemData.length + caPemDataLenData.length);

let certChainData: cert.CertChainData = {
  data: certChainBuff,
  // Number of certificates in the certificate chain. It must be set based on the service.
  count: 2,
  // Assign a value based on the encodingData format. FORMAT_PEM and FORMAT_DER are supported.
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

try {
  let validator = cert.createCertChainValidator('PKIX');
  validator.validate(certChainData, (error, _data) => {
    if (error) {
      console.error(`validate failed, errCode: ${error.code}, errMsg: ${error.message}`);
    } else {
      console.info('validate result: success.');
    }
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`validate failed, errCode: ${e.code}, errMsg: ${e.message}`);
}
```

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

// Certificate chain data.
let certPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIDTjCCAjagAwIBAgIBBDANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDQwMVoXDTM0MDMxNzAyMDQwMVowEjEQMA4GA1UEAwwH\n' +
  'ZGV2aWNlMjCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAMIXL3e7UE/c\n' +
  'Z1dPVgRZ5L8gsQ/azuYVBvoFf7o8ksYrL7G1+qZIJjVRqZkuTirLW4GicbkIkPNW\n' +
  'eix5cDhkjkC+q5SBCOrSSTTlvX3xcOY1gMlA5MgeBfGixFusq4d5VPF2KceZ20/a\n' +
  'ygwGD0Uv0X81OERyPom/dYdJUvfaD9ifPFJ1fKIj/cPFG3yJK/ojpEfndZNdESQL\n' +
  'TkoDekilg2UGOLtY6fb9Ns37ncuIj33gCS/R9m1tgtmqCTcgOQ4hwKhjVF3InmPO\n' +
  '2BbWKvD1RUX+rHC2a2HHDQILOOtDTy8dHvE+qZlK0efrpRgoFEERJAGPi1GDGWiA\n' +
  '7UX1c4MCxIECAwEAAaOBrjCBqzAJBgNVHRMEAjAAMB0GA1UdDgQWBBQbkAcMT7ND\n' +
  'fGp3VPFzYHppZ1zxLTAfBgNVHSMEGDAWgBR0W/koCbvDtFGHUQZLM3j6HKsW2DAd\n' +
  'BgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwCwYDVR0PBAQDAgeAMDIGCCsG\n' +
  'AQUFBwEBBCYwJDAiBggrBgEFBQcwAYYWaHR0cHM6Ly8xMjcuMC4wLjE6OTk5OTAN\n' +
  'BgkqhkiG9w0BAQsFAAOCAQEAF1OTzTmbklFOdZCxrF3zg9owUPJR5RB+PbuBlUfI\n' +
  '8tkGXkMltQ8PN1dv6Cq+d8BluiJdWEzqVoJa/e5SHHJyYQSOhlurRG0GBXllVQ1I\n' +
  'n1PFaI40+9X2X6wrEcdC5nbzogR1jSiksCiTcARMddj0Xrp5FMrFaaGY8M/xqzdW\n' +
  'LTDl4nfbuxtA71cIjnE4kOcaemly9/S2wYWdPktsPxQPY1nPUOeJFI7o0sH3rK0c\n' +
  'JSqtgAG8vnjK+jbx9RpkgqCsXgUbIahL573VTgxrNrsRjCuVal7XVxl/xOKXr6Er\n' +
  'Gpc+OCrXbHNZkUQE5fZH3yL2tXd7EASEb6J3aEWHfF8YBA==\n' +
  '-----END CERTIFICATE-----';

let caPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIC/zCCAeegAwIBAgIBATANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDIyNFoXDTM0MDMxNzAyMDIyNFowEjEQMA4GA1UEAwwH\n' +
  'Um9vdCBDQTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALxI5SDvRfKU\n' +
  '6XaTeyh2LHlUK0rVSeYfXkYf5Mc3Pgucg+ewzQjxkACMx5NYaW1zfGDNPG1i5IZl\n' +
  'cPeWNz1Tm2g6wTd+LyNoNOOmwfLV8pLXSfAukgNrBREf3BzVrbu7hvPd2MmLH23H\n' +
  'OBM9uDPTIqu3n2CDN2EzwULjaSk2g+jvhVKsDLInu5uKPmZBFhs1FWKgcnVnlbi1\n' +
  'AyAx4efheits6EO70oV6UufCEtS1VsBXQHZRAG4ogshWldRBVNxkU6yHAfg0mM/5\n' +
  'EhrZsfh51fWqlrhNWrInjgNV3xIt5ebTIgKZWUlSVHEA/UqDoGfY+CsAJdteZWOW\n' +
  'KjsrC/DK2O0CAwEAAaNgMF4wHQYDVR0OBBYEFHRb+SgJu8O0UYdRBkszePocqxbY\n' +
  'MB8GA1UdIwQYMBaAFHRb+SgJu8O0UYdRBkszePocqxbYMA8GA1UdEwEB/wQFMAMB\n' +
  'Af8wCwYDVR0PBAQDAgEGMA0GCSqGSIb3DQEBCwUAA4IBAQAKOT1ObfQNMN2wdfHq\n' +
  'PQgFDDp6rBMbZe70LswPirSXljo4S/vfbG+gBoWCdu/SfsV+lyP75kg1wX0IQvzW\n' +
  'xYNh864dgqPmGd0v8TIfM0UT0PpnowUyBHQ+E7LNYIOh/kjHbl3oERdEFA2PUyE9\n' +
  'j3GLdg8oe/LqhEQCSAlH+v2RQgBZ9eVN+mSdUxwywm9U3acb0uqVkGiWK/ywumpg\n' +
  'AmIZLMJtMVvg8uDkfy16Z4lChTEdNaJVUqPczUNk2kHXIF4we4be9HoOuTVz/SD/\n' +
  'IsOhXn/BjS3jnhyS9fxo+opJf9zVTWI02Hlh1WVVtH/m3nIZblyAJhcjCHA2wZSz\n' +
  'sSus\n' +
  '-----END CERTIFICATE-----';

let certPemData = stringToUint8Array(certPem);
let caPemData = stringToUint8Array(caPem);

let certPemDataLenData = new Uint8Array(new Uint16Array([certPemData.length]).buffer);
let caPemDataLenData = new Uint8Array(new Uint16Array([caPemData.length]).buffer);

let certChainBuff =
  new Uint8Array(certPemDataLenData.length + certPemData.length + caPemDataLenData.length + caPemData.length);
certChainBuff.set(certPemDataLenData);
certChainBuff.set(certPemData, certPemDataLenData.length);
certChainBuff.set(caPemDataLenData, certPemDataLenData.length + certPemData.length);
certChainBuff.set(caPemData, certPemDataLenData.length + certPemData.length + caPemDataLenData.length);

let certChainData: cert.CertChainData = {
  data: certChainBuff,
  // Number of certificates in the certificate chain. It must be set based on the service.
  count: 2,
  // Assign a value based on the encodingData format. FORMAT_PEM and FORMAT_DER are supported.
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

try {
  let validator = cert.createCertChainValidator('PKIX');
  validator.validate(certChainData).then(_result => {
    console.info('validate result: success.');
  }).catch((error: BusinessError) => {
    console.error(`validate failed, errCode: ${error.code}, errMsg: ${error.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`validate failed, errCode: ${e.code}, errMsg: ${e.message}`);
}
```

## validate

```TypeScript
validate(certChain: CertChainData): Promise<void>
```

Validates an X.509 certificate chain. This API uses a promise to return the result.

<br>Because the system time on the device is untrusted, the certificate chain validator does not verify the certificate validity period. To check the validity period of a certificate, use the [checkValidityWithDate()](arkts-devicecertificate-cert-x509cert-i.md#checkvaliditywithdate) API of the **X509Cert** class. For details about certificate specifications, see [Certificate Specifications](../../../security/DeviceCertificateKit/certificate-framework-overview.md#certificate-specifications).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| certChain | [CertChainData](arkts-devicecertificate-cert-certchaindata-i.md) | Yes | Serialized X.509 certificate chain data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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

// Binary data of the certificate chain.
let certPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIDTjCCAjagAwIBAgIBBDANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDQwMVoXDTM0MDMxNzAyMDQwMVowEjEQMA4GA1UEAwwH\n' +
  'ZGV2aWNlMjCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAMIXL3e7UE/c\n' +
  'Z1dPVgRZ5L8gsQ/azuYVBvoFf7o8ksYrL7G1+qZIJjVRqZkuTirLW4GicbkIkPNW\n' +
  'eix5cDhkjkC+q5SBCOrSSTTlvX3xcOY1gMlA5MgeBfGixFusq4d5VPF2KceZ20/a\n' +
  'ygwGD0Uv0X81OERyPom/dYdJUvfaD9ifPFJ1fKIj/cPFG3yJK/ojpEfndZNdESQL\n' +
  'TkoDekilg2UGOLtY6fb9Ns37ncuIj33gCS/R9m1tgtmqCTcgOQ4hwKhjVF3InmPO\n' +
  '2BbWKvD1RUX+rHC2a2HHDQILOOtDTy8dHvE+qZlK0efrpRgoFEERJAGPi1GDGWiA\n' +
  '7UX1c4MCxIECAwEAAaOBrjCBqzAJBgNVHRMEAjAAMB0GA1UdDgQWBBQbkAcMT7ND\n' +
  'fGp3VPFzYHppZ1zxLTAfBgNVHSMEGDAWgBR0W/koCbvDtFGHUQZLM3j6HKsW2DAd\n' +
  'BgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwCwYDVR0PBAQDAgeAMDIGCCsG\n' +
  'AQUFBwEBBCYwJDAiBggrBgEFBQcwAYYWaHR0cHM6Ly8xMjcuMC4wLjE6OTk5OTAN\n' +
  'BgkqhkiG9w0BAQsFAAOCAQEAF1OTzTmbklFOdZCxrF3zg9owUPJR5RB+PbuBlUfI\n' +
  '8tkGXkMltQ8PN1dv6Cq+d8BluiJdWEzqVoJa/e5SHHJyYQSOhlurRG0GBXllVQ1I\n' +
  'n1PFaI40+9X2X6wrEcdC5nbzogR1jSiksCiTcARMddj0Xrp5FMrFaaGY8M/xqzdW\n' +
  'LTDl4nfbuxtA71cIjnE4kOcaemly9/S2wYWdPktsPxQPY1nPUOeJFI7o0sH3rK0c\n' +
  'JSqtgAG8vnjK+jbx9RpkgqCsXgUbIahL573VTgxrNrsRjCuVal7XVxl/xOKXr6Er\n' +
  'Gpc+OCrXbHNZkUQE5fZH3yL2tXd7EASEb6J3aEWHfF8YBA==\n' +
  '-----END CERTIFICATE-----';

let caPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIC/zCCAeegAwIBAgIBATANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDIyNFoXDTM0MDMxNzAyMDIyNFowEjEQMA4GA1UEAwwH\n' +
  'Um9vdCBDQTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALxI5SDvRfKU\n' +
  '6XaTeyh2LHlUK0rVSeYfXkYf5Mc3Pgucg+ewzQjxkACMx5NYaW1zfGDNPG1i5IZl\n' +
  'cPeWNz1Tm2g6wTd+LyNoNOOmwfLV8pLXSfAukgNrBREf3BzVrbu7hvPd2MmLH23H\n' +
  'OBM9uDPTIqu3n2CDN2EzwULjaSk2g+jvhVKsDLInu5uKPmZBFhs1FWKgcnVnlbi1\n' +
  'AyAx4efheits6EO70oV6UufCEtS1VsBXQHZRAG4ogshWldRBVNxkU6yHAfg0mM/5\n' +
  'EhrZsfh51fWqlrhNWrInjgNV3xIt5ebTIgKZWUlSVHEA/UqDoGfY+CsAJdteZWOW\n' +
  'KjsrC/DK2O0CAwEAAaNgMF4wHQYDVR0OBBYEFHRb+SgJu8O0UYdRBkszePocqxbY\n' +
  'MB8GA1UdIwQYMBaAFHRb+SgJu8O0UYdRBkszePocqxbYMA8GA1UdEwEB/wQFMAMB\n' +
  'Af8wCwYDVR0PBAQDAgEGMA0GCSqGSIb3DQEBCwUAA4IBAQAKOT1ObfQNMN2wdfHq\n' +
  'PQgFDDp6rBMbZe70LswPirSXljo4S/vfbG+gBoWCdu/SfsV+lyP75kg1wX0IQvzW\n' +
  'xYNh864dgqPmGd0v8TIfM0UT0PpnowUyBHQ+E7LNYIOh/kjHbl3oERdEFA2PUyE9\n' +
  'j3GLdg8oe/LqhEQCSAlH+v2RQgBZ9eVN+mSdUxwywm9U3acb0uqVkGiWK/ywumpg\n' +
  'AmIZLMJtMVvg8uDkfy16Z4lChTEdNaJVUqPczUNk2kHXIF4we4be9HoOuTVz/SD/\n' +
  'IsOhXn/BjS3jnhyS9fxo+opJf9zVTWI02Hlh1WVVtH/m3nIZblyAJhcjCHA2wZSz\n' +
  'sSus\n' +
  '-----END CERTIFICATE-----';

let certPemData = stringToUint8Array(certPem);
let caPemData = stringToUint8Array(caPem);

let certPemDataLenData = new Uint8Array(new Uint16Array([certPemData.length]).buffer);
let caPemDataLenData = new Uint8Array(new Uint16Array([caPemData.length]).buffer);

let certChainBuff =
  new Uint8Array(certPemDataLenData.length + certPemData.length + caPemDataLenData.length + caPemData.length);
certChainBuff.set(certPemDataLenData);
certChainBuff.set(certPemData, certPemDataLenData.length);
certChainBuff.set(caPemDataLenData, certPemDataLenData.length + certPemData.length);
certChainBuff.set(caPemData, certPemDataLenData.length + certPemData.length + caPemDataLenData.length);

let certChainData: cert.CertChainData = {
  data: certChainBuff,
  // Number of certificates in the certificate chain. It must be set based on the service.
  count: 2,
  // Assign a value based on the encodingData format. FORMAT_PEM and FORMAT_DER are supported.
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

try {
  let validator = cert.createCertChainValidator('PKIX');
  validator.validate(certChainData, (error, _data) => {
    if (error) {
      console.error(`validate failed, errCode: ${error.code}, errMsg: ${error.message}`);
    } else {
      console.info('validate result: success.');
    }
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`validate failed, errCode: ${e.code}, errMsg: ${e.message}`);
}
```

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

// Certificate chain data.
let certPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIDTjCCAjagAwIBAgIBBDANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDQwMVoXDTM0MDMxNzAyMDQwMVowEjEQMA4GA1UEAwwH\n' +
  'ZGV2aWNlMjCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAMIXL3e7UE/c\n' +
  'Z1dPVgRZ5L8gsQ/azuYVBvoFf7o8ksYrL7G1+qZIJjVRqZkuTirLW4GicbkIkPNW\n' +
  'eix5cDhkjkC+q5SBCOrSSTTlvX3xcOY1gMlA5MgeBfGixFusq4d5VPF2KceZ20/a\n' +
  'ygwGD0Uv0X81OERyPom/dYdJUvfaD9ifPFJ1fKIj/cPFG3yJK/ojpEfndZNdESQL\n' +
  'TkoDekilg2UGOLtY6fb9Ns37ncuIj33gCS/R9m1tgtmqCTcgOQ4hwKhjVF3InmPO\n' +
  '2BbWKvD1RUX+rHC2a2HHDQILOOtDTy8dHvE+qZlK0efrpRgoFEERJAGPi1GDGWiA\n' +
  '7UX1c4MCxIECAwEAAaOBrjCBqzAJBgNVHRMEAjAAMB0GA1UdDgQWBBQbkAcMT7ND\n' +
  'fGp3VPFzYHppZ1zxLTAfBgNVHSMEGDAWgBR0W/koCbvDtFGHUQZLM3j6HKsW2DAd\n' +
  'BgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwCwYDVR0PBAQDAgeAMDIGCCsG\n' +
  'AQUFBwEBBCYwJDAiBggrBgEFBQcwAYYWaHR0cHM6Ly8xMjcuMC4wLjE6OTk5OTAN\n' +
  'BgkqhkiG9w0BAQsFAAOCAQEAF1OTzTmbklFOdZCxrF3zg9owUPJR5RB+PbuBlUfI\n' +
  '8tkGXkMltQ8PN1dv6Cq+d8BluiJdWEzqVoJa/e5SHHJyYQSOhlurRG0GBXllVQ1I\n' +
  'n1PFaI40+9X2X6wrEcdC5nbzogR1jSiksCiTcARMddj0Xrp5FMrFaaGY8M/xqzdW\n' +
  'LTDl4nfbuxtA71cIjnE4kOcaemly9/S2wYWdPktsPxQPY1nPUOeJFI7o0sH3rK0c\n' +
  'JSqtgAG8vnjK+jbx9RpkgqCsXgUbIahL573VTgxrNrsRjCuVal7XVxl/xOKXr6Er\n' +
  'Gpc+OCrXbHNZkUQE5fZH3yL2tXd7EASEb6J3aEWHfF8YBA==\n' +
  '-----END CERTIFICATE-----';

let caPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIC/zCCAeegAwIBAgIBATANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDIyNFoXDTM0MDMxNzAyMDIyNFowEjEQMA4GA1UEAwwH\n' +
  'Um9vdCBDQTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALxI5SDvRfKU\n' +
  '6XaTeyh2LHlUK0rVSeYfXkYf5Mc3Pgucg+ewzQjxkACMx5NYaW1zfGDNPG1i5IZl\n' +
  'cPeWNz1Tm2g6wTd+LyNoNOOmwfLV8pLXSfAukgNrBREf3BzVrbu7hvPd2MmLH23H\n' +
  'OBM9uDPTIqu3n2CDN2EzwULjaSk2g+jvhVKsDLInu5uKPmZBFhs1FWKgcnVnlbi1\n' +
  'AyAx4efheits6EO70oV6UufCEtS1VsBXQHZRAG4ogshWldRBVNxkU6yHAfg0mM/5\n' +
  'EhrZsfh51fWqlrhNWrInjgNV3xIt5ebTIgKZWUlSVHEA/UqDoGfY+CsAJdteZWOW\n' +
  'KjsrC/DK2O0CAwEAAaNgMF4wHQYDVR0OBBYEFHRb+SgJu8O0UYdRBkszePocqxbY\n' +
  'MB8GA1UdIwQYMBaAFHRb+SgJu8O0UYdRBkszePocqxbYMA8GA1UdEwEB/wQFMAMB\n' +
  'Af8wCwYDVR0PBAQDAgEGMA0GCSqGSIb3DQEBCwUAA4IBAQAKOT1ObfQNMN2wdfHq\n' +
  'PQgFDDp6rBMbZe70LswPirSXljo4S/vfbG+gBoWCdu/SfsV+lyP75kg1wX0IQvzW\n' +
  'xYNh864dgqPmGd0v8TIfM0UT0PpnowUyBHQ+E7LNYIOh/kjHbl3oERdEFA2PUyE9\n' +
  'j3GLdg8oe/LqhEQCSAlH+v2RQgBZ9eVN+mSdUxwywm9U3acb0uqVkGiWK/ywumpg\n' +
  'AmIZLMJtMVvg8uDkfy16Z4lChTEdNaJVUqPczUNk2kHXIF4we4be9HoOuTVz/SD/\n' +
  'IsOhXn/BjS3jnhyS9fxo+opJf9zVTWI02Hlh1WVVtH/m3nIZblyAJhcjCHA2wZSz\n' +
  'sSus\n' +
  '-----END CERTIFICATE-----';

let certPemData = stringToUint8Array(certPem);
let caPemData = stringToUint8Array(caPem);

let certPemDataLenData = new Uint8Array(new Uint16Array([certPemData.length]).buffer);
let caPemDataLenData = new Uint8Array(new Uint16Array([caPemData.length]).buffer);

let certChainBuff =
  new Uint8Array(certPemDataLenData.length + certPemData.length + caPemDataLenData.length + caPemData.length);
certChainBuff.set(certPemDataLenData);
certChainBuff.set(certPemData, certPemDataLenData.length);
certChainBuff.set(caPemDataLenData, certPemDataLenData.length + certPemData.length);
certChainBuff.set(caPemData, certPemDataLenData.length + certPemData.length + caPemDataLenData.length);

let certChainData: cert.CertChainData = {
  data: certChainBuff,
  // Number of certificates in the certificate chain. It must be set based on the service.
  count: 2,
  // Assign a value based on the encodingData format. FORMAT_PEM and FORMAT_DER are supported.
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

try {
  let validator = cert.createCertChainValidator('PKIX');
  validator.validate(certChainData).then(_result => {
    console.info('validate result: success.');
  }).catch((error: BusinessError) => {
    console.error(`validate failed, errCode: ${error.code}, errMsg: ${error.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`validate failed, errCode: ${e.code}, errMsg: ${e.message}`);
}
```

## validateCert

```TypeScript
validateCert(cert: X509Cert, params: CertValidationParams): Promise<CertValidationResult>
```

Validates a certificate by building and verifying its certificate chain. This API uses a promise to return the result.

<br>The certificate chain construction process complies with the following rules:
1. Trusted anchor source: The trusted certificate list (trustedCerts) is always used as the trust anchor source.
The preconfigured certificate is used as the trust anchor source only when trustSystemCa is set to true.
2. Issuer search sequence: The system searches for the issuer from the trust anchor source first. If the issuer
cannot be found, the system searches for the issuer in the untrusted certificate list (untrustedCerts). The intermediate CA certificate downloaded online is an untrusted certificate.
3. Trust anchor locking: Once the issuer is found in the trust anchor source, the subsequent lookup process does
not roll back to the untrusted certificate, that is, the subsequent certificates must come from the trust anchor source.
4. Construction completion conditions:
If partialChain is false (default value), the build is complete only when the root certificate (self-signed certificate) is found. If partialChain is true, the first time the issuer is found in the trust anchor source, the build is complete.
5. Follow-up verification: After the certificate chain is constructed, perform other verification operations,
such as certificate signature verification and certificate revocation check.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cert | [X509Cert](arkts-devicecertificate-cert-x509cert-i.md) | Yes | Certificate to verify. |
| params | [CertValidationParams](arkts-devicecertificate-cert-certvalidationparams-i.md) | Yes | Certificate validation parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CertValidationResult](arkts-devicecertificate-cert-certvalidationresult-i.md)&gt; | Promise used to return the result of certificate validation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-memory-error) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-runtime-error) | Runtime error. Possible causes:<br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19020003](../errorcode-cert.md#19020003-parameter-check-failure) | Parameter check failed. |
| [19030001](../errorcode-cert.md#19030001-failed-to-invoke-the-third-party-cryptographic-api) | Crypto operation error. |
| [19030002](../errorcode-cert.md#19030002-certificate-signature-verification-failed) | The certificate signature verification failed. |
| [19030003](../errorcode-cert.md#19030003-certificate-has-not-taken-effect) | The certificate has not taken effect. |
| [19030004](../errorcode-cert.md#19030004-certificate-expired) | The certificate has expired. |
| [19030005](../errorcode-cert.md#19030005-failed-to-obtain-the-certificate-issuer) | Failed to obtain the certificate issuer. |
| [19030006](../errorcode-cert.md#19030006-key-cannot-be-used-for-signing-a-certificate) | The key cannot be used for signing a certificate. |
| [19030007](../errorcode-cert.md#19030007-key-cannot-be-used-for-digital-signature) | The key cannot be used for a digital signature. |
| [19030009](../errorcode-cert.md#19030009-untrusted-certificate) | Untrusted certificate. |
| [19030010](../errorcode-cert.md#19030010-certificate-revoked) | The certificate has been revoked. |
| [19030011](../errorcode-cert.md#19030011-unknown-key-extensions) | Unsupported critical extension. |
| [19030012](../errorcode-cert.md#19030012-host-name-mismatch) | Hostname mismatch in the certificate. |
| [19030013](../errorcode-cert.md#19030013-email-address-mismatch) | Email address mismatch in the certificate. |
| [19030014](../errorcode-cert.md#19030014-key-usage-mismatch) | Key usage mismatch in the certificate. |
| [19030015](../errorcode-cert.md#19030015-failed-to-obtain-the-crl) | Failed to obtain the certificate revocation list. |
| [19030016](../errorcode-cert.md#19030016-invalid-crl) | The certificate revocation list has not taken effect. |
| [19030017](../errorcode-cert.md#19030017-crl-has-expired) | The certificate revocation list has expired. |
| [19030018](../errorcode-cert.md#19030018-failed-to-verify-the-crl-signature) | Failed to verify the signature of the certificate revocation list. |
| [19030019](../errorcode-cert.md#19030019-failed-to-obtain-the-crl-issuer) | Failed to find the issuer of the certificate revocation list. |
| [19030020](../errorcode-cert.md#19030020-failed-to-obtain-the-ocsp-response) | Failed to obtain the OCSP response. |
| [19030021](../errorcode-cert.md#19030021-invalid-ocsp-response) | Invalid OCSP response. |
| [19030022](../errorcode-cert.md#19030022-ocsp-signature-verification-failure) | Failed to verify the OCSP signature. |
| [19030023](../errorcode-cert.md#19030023-unknown-ocsp-certificate-status) | Unknown OCSP certificate status. |
| [19030024](../errorcode-cert.md#19030024-network-connection-timeout) | Network connection timed out. |

**Examples**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// EC P-256 certificate chain data
const endEntityCertPem = '-----BEGIN CERTIFICATE-----\n' +
    'MIICwzCCAmmgAwIBAgIUIThWddD/8p7w5QyXOoRY05O61FMwCgYIKoZIzj0EAwIw\n' +
    'gYsxCzAJBgNVBAYTAkNOMRAwDgYDVQQIDAdCZWlqaW5nMRAwDgYDVQQHDAdCZWlq\n' +
    'aW5nMRowGAYDVQQKDBFUZXN0IE9yZ2FuaXphdGlvbjEdMBsGA1UECwwUVGVzdCBJ\n' +
    'bnRlcm1lZGlhdGUgQ0ExHTAbBgNVBAMMFFRlc3QgSW50ZXJtZWRpYXRlIENBMB4X\n' +
    'DTI2MDMzMTA4MjY1OFoXDTI3MDMzMTA4MjY1OFowgYIxCzAJBgNVBAYTAkNOMRAw\n' +
    'DgYDVQQIDAdCZWlqaW5nMRAwDgYDVQQHDAdCZWlqaW5nMRowGAYDVQQKDBFUZXN0\n' +
    'IE9yZ2FuaXphdGlvbjEYMBYGA1UECwwPVGVzdCBEZXBhcnRtZW50MRkwFwYDVQQD\n' +
    'DBB0ZXN0LmV4YW1wbGUuY29tMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEspH8\n' +
    'JVcqNrg7oP4PYHADsW8tc1kIF86JG5SSjh1fz4ja3dF98PMMrsbQtcBZiwp8rD5e\n' +
    'Gp2Nv/C2ymnjJfrig6OBsTCBrjAJBgNVHRMEAjAAMA4GA1UdDwEB/wQEAwIFoDAd\n' +
    'BgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwHQYDVR0OBBYEFH6aJ7ZQayEZ\n' +
    'LeenLt7zowBoafRpMB8GA1UdIwQYMBaAFI2lMRV2YgzF/DBP92jUzOLdzSDdMDIG\n' +
    'A1UdEQQrMCmCEHRlc3QuZXhhbXBsZS5jb22CD3d3dy5leGFtcGxlLmNvbYcEfwAA\n' +
    'ATAKBggqhkjOPQQDAgNIADBFAiEAidnsForpQc9qTBpa68YEYS0TQRUySHaUB/pr\n' +
    'PNfAYqECIGGKM44mqQgSvZyYQHnlnu3jkbHpFJTaQBAvz9B1jFuc\n' +
    '-----END CERTIFICATE-----\n';

const intermediateCaPem = '-----BEGIN CERTIFICATE-----\n' +
    'MIICbzCCAhWgAwIBAgIUI8/xor2S98OupuBX6hWevxhvK+wwCgYIKoZIzj0EAwIw\n' +
    'ezELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0JlaWpp\n' +
    'bmcxGjAYBgNVBAoMEVRlc3QgT3JnYW5pemF0aW9uMRUwEwYDVQQLDAxUZXN0IFJv\n' +
    'b3QgQ0ExFTATBgNVBAMMDFRlc3QgUm9vdCBDQTAeFw0yNjAzMzEwODI2NThaFw0z\n' +
    'MTAzMzAwODI2NThaMIGLMQswCQYDVQQGEwJDTjEQMA4GA1UECAwHQmVpamluZzEQ\n' +
    'MA4GA1UEBwwHQmVpamluZzEaMBgGA1UECgwRVGVzdCBPcmdhbml6YXRpb24xHTAb\n' +
    'BgNVBAsMFFRlc3QgSW50ZXJtZWRpYXRlIENBMR0wGwYDVQQDDBRUZXN0IEludGVy\n' +
    'bWVkaWF0ZSBDQTBZMBMGByqGSM49AgEGCCqGSM49AwEHA0IABER6WRsCn7Bh3v8c\n' +
    'k6PIkLeM+ot5l0A46XJdfvuJco58ifzBHjtu4kFOkZTA9F0Hb6JefG590CK5ddiD\n' +
    'g5lOHwKjZjBkMBIGA1UdEwEB/wQIMAYBAf8CAQAwDgYDVR0PAQH/BAQDAgEGMB0G\n' +
    'A1UdDgQWBBSNpTEVdmIMxfwwT/do1Mzi3c0g3TAfBgNVHSMEGDAWgBS/nd4dYdW3\n' +
    'zFxQ1pl2U8I/bfUA3zAKBggqhkjOPQQDAgNIADBFAiEA87NkGCv47e5RWc8DsFd/\n' +
    'zL6/2Xn2EoveC+HoUYpxhZMCIAG+ZuTLmUsjalUGbWyR101hxHfvr4ImbEMeYSaA\n' +
    'sVBn\n' +
    '-----END CERTIFICATE-----\n';

const rootCaPem = '-----BEGIN CERTIFICATE-----\n' +
    'MIICWzCCAgGgAwIBAgIUd/I1bFJJw/xQtPEJP6C1E4Fj9jswCgYIKoZIzj0EAwIw\n' +
    'ezELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0JlaWpp\n' +
    'bmcxGjAYBgNVBAoMEVRlc3QgT3JnYW5pemF0aW9uMRUwEwYDVQQLDAxUZXN0IFJv\n' +
    'b3QgQ0ExFTATBgNVBAMMDFRlc3QgUm9vdCBDQTAeFw0yNjAzMzEwODI2NTdaFw0z\n' +
    'NjAzMjgwODI2NTdaMHsxCzAJBgNVBAYTAkNOMRAwDgYDVQQIDAdCZWlqaW5nMRAw\n' +
    'DgYDVQQHDAdCZWlqaW5nMRowGAYDVQQKDBFUZXN0IE9yZ2FuaXphdGlvbjEVMBMG\n' +
    'A1UECwwMVGVzdCBSb290IENBMRUwEwYDVQQDDAxUZXN0IFJvb3QgQ0EwWTATBgcq\n' +
    'hkjOPQIBBggqhkjOPQMBBwNCAASFeWawqQET+c6EowNooKYiTw1KPzJBgssxQXo7\n' +
    'UEXSQnLHh8sBwVvNN4oFVFImT31DyJVKwxBXpwbrEN1s8J1Io2MwYTAPBgNVHRMB\n' +
    'Af8EBTADAQH/MA4GA1UdDwEB/wQEAwIBBjAdBgNVHQ4EFgQUv53eHWHVt8xcUNaZ\n' +
    'dlPCP231AN8wHwYDVR0jBBgwFoAUv53eHWHVt8xcUNaZdlPCP231AN8wCgYIKoZI\n' +
    'zj0EAwIDSAAwRQIhAIbyIrOZL1GhkRiI2i4IhKmFa4AoXJftTEA5wev99QpkAiA3\n' +
    'khFrJ4rRSpHqbfGN1U14HkFKiCXBalaIe+NISxgC3Q==\n' +
    '-----END CERTIFICATE-----\n';

// Convert the string into a Uint8Array.
function stringToUint8Array(str: string): Uint8Array {
  let arr: Array<number> = [];
  for (let i = 0, j = str.length; i < j; i++) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

async function validateCert(): Promise<void> {
  try {
    // Create an endEntityCertPem object.
    let certEncodingBlob: cert.EncodingBlob = {
      data: stringToUint8Array(endEntityCertPem),
      encodingFormat: cert.EncodingFormat.FORMAT_PEM
    };
    let x509Cert = await cert.createX509Cert(certEncodingBlob);

    // Create a trust anchor certificate (root CA).
    let rootCaEncodingBlob: cert.EncodingBlob = {
      data: stringToUint8Array(rootCaPem),
      encodingFormat: cert.EncodingFormat.FORMAT_PEM
    };
    let rootCaCert = await cert.createX509Cert(rootCaEncodingBlob);

    // Create an intermediate certificate.
    let intermediateCaEncodingBlob: cert.EncodingBlob = {
      data: stringToUint8Array(intermediateCaPem),
      encodingFormat: cert.EncodingFormat.FORMAT_PEM
    };
    let intermediateCaCert = await cert.createX509Cert(intermediateCaEncodingBlob);

    // Set verification parameters.
    let params: cert.CertValidationParams = {
      trustedCerts: [rootCaCert],
      untrustedCerts: [intermediateCaCert],
      validateDate: false
    };

    // Create a validator and verify the certificate.
    let validator = cert.createCertChainValidator('PKIX');
    let result = await validator.validateCert(x509Cert, params);

    console.info('Certificate validation succeeded!');
    console.info(`Verified chain length: ${result.certChain.length}`);
    for (let i = 0; i < result.certChain.length; i++) {
      let subject = result.certChain[i].getSubjectX500DistinguishedName().getName(cert.EncodingType.ENCODING_UTF8);
      console.info(`Cert ${i}: ${subject}`);
    }
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`validate failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

validateCert();
```

## algorithm

```TypeScript
readonly algorithm: string
```

Algorithm used by the X.509 certificate chain validator.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert
