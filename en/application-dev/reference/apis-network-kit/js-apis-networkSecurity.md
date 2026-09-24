# @ohos.net.networkSecurity (Network Security)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=108aa11c2ceb50c68f8417aa3c60f1dcb55dabdd translatedAt=2026-09-23T02:35:42.096Z pushedAt=2026-09-24T06:00:14.218Z -->

The **networkSecurity** module provides the network security verification capability. Specifically, it provides APIs for applications to verify the certificates in use.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { networkSecurity } from '@kit.NetworkKit';
```

## Sample Code

```ts
import { networkSecurity } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Define certificate blobs
const cert: networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (certificate data) ...\n-----END CERTIFICATE-----',
};

const caCert: networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (CA certificate data) ...\n-----END CERTIFICATE-----',
};

// Perform asynchronous certificate verification
networkSecurity.certVerification(cert, caCert)
  .then((result) => {
    console.info('Certificate verification result:', result);
  })
  .catch((error: BusinessError) => {
    console.error('Certificate verification failed:', error);
  });
```

> **NOTE**
> 
> Be sure to replace the certificate data in the example with the actual certificate data.

## CertType

Enumerates certificate types.

**System capability**: SystemCapability.Communication.NetStack

| Name         | Value   |      Description    |
| ------------- | ----- | ------------- |
| CERT_TYPE_PEM | 0     | PEM certificate|
| CERT_TYPE_DER | 1     | DER certificate.|


## CertBlob

Defines the certificate data.

**System capability**: SystemCapability.Communication.NetStack

| Name | Type                  | Read-Only     |Optional| Description          |
| ----- | --------------------- | --------- | ----|---------- |
| type  | [CertType](#certtype) | No    | No | Certificate encoding type.  |
| data  | string \| ArrayBuffer | No   | No|Certificate data.     |


## networkSecurity.certVerification

certVerification(cert: CertBlob, caCert?: CertBlob): Promise\<number\>

Verifies the certificate passed by the application using the preset CA certificate and the CA certificate installed by the user in the certificate management. This API uses a promise to return the result.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name| Type    | Mandatory| Description                  |
| ------ | -------- | ---- | ---------------------- |
| cert   | [CertBlob](#certblob) | Yes   | Certificate to be verified.       |
| caCert | [CertBlob](#certblob) | No   | Custom CA certificate passed in. |

**Return values:**

| Type           | Description                                                        |
| --------------- | ------------------------------------------------------------ |
| Promise\<number\> | Promise object that returns a number indicating the certificate verification result. The value **0** indicates that the certificate verification is successful; otherwise, the verification fails. |

**Error codes**

For details about the error codes, see [Network Security Error Codes](errorcode-net-networkSecurity.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                            |
| -------- | ---------------------------------------------------- |
| 401      | Parameter error.                                     |
| 2305001  | Unspecified error.                                   |
| 2305002  | Unable to get issuer certificate.                    |
| 2305003  | Unable to get certificate revocation list (CRL).     |
| 2305004  | Unable to decrypt certificate signature.             |
| 2305005  | Unable to decrypt CRL signature.                     |
| 2305006  | Unable to decode issuer public key.                  |
| 2305007  | Certificate signature failure.                       |
| 2305008  | CRL signature failure.                               |
| 2305009  | Certificate is not yet valid.                        |
| 2305010  | Certificate has expired.                             |
| 2305011  | CRL is not yet valid.                                |
| 2305012  | CRL has expired.                                     |
| 2305018  | Self-signed certificate. <br>Applicable versions: 12+ |
| 2305023  | Certificate has been revoked.                        |
| 2305024  | Invalid certificate authority (CA).                  |
| 2305027  | Certificate is untrusted.                            |
| 2305069  | Invalid certificate verification context. <br>Applicable versions: 12+ |

> **NOTE**
> 
> The preceding error codes indicate errors that may occur during certificate verification.

**Example**

```ts
import { networkSecurity } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Define certificate blobs
const cert:networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (certificate data) ...\n-----END CERTIFICATE-----',
};

const caCert:networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (CA certificate data) ...\n-----END CERTIFICATE-----',
};

// Perform asynchronous certificate verification
networkSecurity.certVerification(cert, caCert)
  .then((result) => {
    console.info('Certificate verification result:', result);
  })
  .catch((error: BusinessError) => {
    console.error('Certificate verification failed:', error);
  });
```
> **NOTE**
> 
> Be sure to replace the certificate data in the example with the actual certificate data.



## networkSecurity.certVerificationSync

certVerificationSync(cert: CertBlob, caCert?: CertBlob): number

Verifies the certificate passed by the application using the preset CA certificate and the CA certificate installed by the user in the certificate management. This API returns the result synchronously.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name| Type    | Mandatory| Description                  |
| ------ | -------- | ---- | ---------------------- |
| cert   | [CertBlob](#certblob) | Yes  | Certificate to be verified.       |
| caCert | [CertBlob](#certblob) | No   | Custom CA certificate passed in. |

**Return values:**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| number | Indicates the result of certificate verification. If the certificate verification succeeds, **0** is returned; otherwise, the verification fails. |

**Error codes**

For details about the error codes, see [Network Security Error Codes](errorcode-net-networkSecurity.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                            |
| -------- | ---------------------------------------------------- |
| 401      | Parameter error.                                     |
| 2305001  | Unspecified error.                                   |
| 2305002  | Unable to get issuer certificate.                    |
| 2305003  | Unable to get certificate revocation list (CRL).     |
| 2305004  | Unable to decrypt certificate signature.             |
| 2305005  | Unable to decrypt CRL signature.                     |
| 2305006  | Unable to decode issuer public key.                  |
| 2305007  | Certificate signature failure.                       |
| 2305008  | CRL signature failure.                               |
| 2305009  | Certificate is not yet valid.                        |
| 2305010  | Certificate has expired.                             |
| 2305011  | CRL is not yet valid.                                |
| 2305012  | CRL has expired.                                     |
| 2305018  | Self-signed certificate. <br>Applicable versions: 12+ |
| 2305023  | Certificate has been revoked.                        |
| 2305024  | Invalid certificate authority (CA).                  |
| 2305027  | Certificate is untrusted.                            |
| 2305069  | Invalid certificate verification context. <br>Applicable versions: 12+ |

> **NOTE**
>
> The preceding error codes indicate errors that may occur during certificate verification.

**Example**

```ts
import { networkSecurity } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create certificate blobs
const cert: networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n...'
};

const caCert: networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n...'
};

// Asynchronous verification
networkSecurity.certVerification(cert, caCert)
  .then((result) => {
    console.info('Verification Result:', result);
  })
  .catch((error: BusinessError) => {
    console.error('Verification Error:', error);
  });

// Synchronous verification
let resultSync: number = networkSecurity.certVerificationSync(cert, caCert);
console.info('Synchronous Verification Result:', resultSync);
```

> **NOTE**
>
> Be sure to replace the certificate data in the example with the actual certificate data.

## networkSecurity.verifyCertChain

verifyCertChain(cert: CertBlob\[\], caCert?: CertBlob, hostname?: string): Promise\<CertBlob\[\]\>

Passes in an array of certificates, verifies the certificate chain, and builds a sorted certificate chain. The system uses the preset CA certificates in certificate management and the CA certificates installed by users to verify the passed-in certificates. This API uses a promise to return the result asynchronously.

**Since:** 26.0.0

**System capability**: SystemCapability.Communication.NetStack

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type     | Mandatory | Description                   |
| ------ | -------- | ---- | ---------------------- |
| cert   | [CertBlob](#certblob)\[\] | Yes   | Array of certificates to verify. The first element must be the end-entity certificate, and the remaining elements are intermediate certificates. |
| caCert | [CertBlob](#certblob) | No   | Custom CA certificate. If this parameter is not passed in, the preset CA certificates of the system are used. |
| hostname | string | No   | Host name to verify, used to check whether the host name in the certificate matches. If this parameter is not passed in, host name verification is skipped. |

**Return value**

| Type            | Description                                                         |
| --------------- | ------------------------------------------------------------ |
| Promise\<[CertBlob](#certblob)\[\]\> | Promise object that returns the sorted certificate chain array, in the order from the leaf node to the root node. |

**Error codes**

For details about the error codes, see [Network Security Verification Error Codes](errorcode-net-networkSecurity.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                             |
| -------- | ---------------------------------------------------- |
| 2305001  | Unspecified error.                                   |
| 2305002  | Unable to get issuer certificate.                    |
| 2305004  | Unable to decrypt certificate signature.             |
| 2305006  | Unable to decode issuer public key.                  |
| 2305007  | Certificate signature failure.                       |
| 2305009  | Certificate is not yet valid.                        |
| 2305010  | Certificate has expired.                             |
| 2305018  | Self-signed certificate.                             |
| 2305024  | Invalid certificate authority (CA).                  |
| 2305027  | Certificate is untrusted.                            |
| 2305062  | Invalid hostname.                                    |
| 2305069  | Invalid certificate verification context.            |

> **NOTE**
> 
> These error codes correspond to various failures in the certificate verification process.

**Example**

```ts
import { networkSecurity } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Define certificate blobs
const cert1: networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (server certificate) ...\n-----END CERTIFICATE-----',
};

const cert2: networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (intermediate certificate) ...\n-----END CERTIFICATE-----',
};

const caCert: networkSecurity.CertBlob = {
  type: networkSecurity.CertType.CERT_TYPE_PEM,
  data: '-----BEGIN CERTIFICATE-----\n... (CA certificate) ...\n-----END CERTIFICATE-----',
};

// Verify and build sorted cert chain
networkSecurity.verifyCertChain([cert1, cert2], caCert, "example.com")
  .then((sortedChain: Array<networkSecurity.CertBlob>) => {
    console.info('Certificate chain verified and sorted, chain length:', sortedChain.length);
    for (let i = 0; i < sortedChain.length; i++) {
      console.info(`Certificate ${i}: type=${sortedChain[i].type}, data=${sortedChain[i].data}`);
    }
  })
  .catch((error: BusinessError) => {
    console.error('Certificate chain verification failed:', error);
  });
```
> **NOTE**
> 
> Be sure to replace the certificate data in the example with the actual certificate content.

## networkSecurity.isCleartextPermitted<sup>18+</sup>

isCleartextPermitted(): boolean

Checks whether plaintext HTTP access is allowed from the preset **network_config.json** file of the application. By default, plaintext HTTP access is allowed.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetStack

**Return values:**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| boolean | Boolean value indicating whether plaintext HTTP is allowed. The value **true** indicates that plaintext HTTP is allowed, and the value **false** indicates the opposite. The default value is **true**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                            |
| -------- | ---------------------------------------------------- |
| 201      | Permission denied.                                  |

**Example**

```ts
import { networkSecurity } from '@kit.NetworkKit';

try {
  let result: boolean = networkSecurity.isCleartextPermitted();
  console.info(`isCleartextPermitted Result: ${JSON.stringify(result)}`);
} catch (error) {
  console.error(`isCleartextPermitted Error: ${JSON.stringify(error)}`);
}
```

## networkSecurity.isCleartextPermittedByHostName<sup>18+</sup>

isCleartextPermittedByHostName(hostName: string): boolean

Checks whether host name–based plaintext HTTP access is allowed from the preset **network_config.json** file of the application. By default, plaintext HTTP access is allowed.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name| Type    | Mandatory| Description                  |
| ------ | -------- | ---- | ---------------------- |
| hostName | string | Yes | Host name.|

**Return values:**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| boolean | Boolean value indicating whether host name–based plaintext HTTP is allowed. The value **true** indicates that plaintext HTTP is allowed, and the value **false** indicates the opposite. The default value is **true**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                            |
| -------- | ---------------------------------------------------- |
| 201      | Permission denied.                                     |

**Example**

```ts
import { networkSecurity } from '@kit.NetworkKit';

try {
  let result: boolean = networkSecurity.isCleartextPermittedByHostName("xxx");
  console.info(`isCleartextPermitted Result: ${JSON.stringify(result)}`);
} catch (error) {
  console.error(`isCleartextPermitted Error: ${JSON.stringify(error)}`);
}
```