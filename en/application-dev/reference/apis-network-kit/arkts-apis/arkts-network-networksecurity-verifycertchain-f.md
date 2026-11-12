# verifyCertChain

## Modules to Import

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
```

## verifyCertChain

```TypeScript
export function verifyCertChain(cert: CertBlob[], caCert?: CertBlob, hostname?: string): Promise<CertBlob[]>
```

Passes in an array of certificates, verifies the certificate chain, and builds a sorted certificate chain. The system uses the preset CA certificates in certificate management and the CA certificates installed by users to verify the passed-in certificates. This API uses a promise to return the result asynchronously.

> **NOTE:** 
> 
> These error codes correspond to various failures in the certificate verification process.
> 
> **NOTE:** 
> 
> Be sure to replace the certificate data in the example with the actual certificate content.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-networkSecurity-export function verifyCertChain(cert: CertBlob[], caCert?: CertBlob, hostname?: string): Promise<CertBlob[]>--><!--Device-networkSecurity-export function verifyCertChain(cert: CertBlob[], caCert?: CertBlob, hostname?: string): Promise<CertBlob[]>-End-->

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cert | [CertBlob](arkts-network-networksecurity-certblob-i.md)[] | Yes | Array of certificates to verify. The first element must be the end-entity certificate, and the remaining elements are intermediate certificates. |
| caCert | [CertBlob](arkts-network-networksecurity-certblob-i.md) | No | Custom CA certificate. If this parameter is not passed in, the preset CA certificates of the system are used. |
| hostname | string | No | Host name to verify, used to check whether the host name in the certificate matches. If this parameter is not passed in, host name verification is skipped. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CertBlob](arkts-network-networksecurity-certblob-i.md)[]&gt; | Promise used to return the sorted certificate chain array, in the order from the leaf node to the root node. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2305001](../errorcode-net-networkSecurity.md#2305001-unspecified-error) | Unspecified error. |
| [2305002](../errorcode-net-networkSecurity.md#2305002-failed-to-obtain-the-issuer-certificate) | Unable to get issuer certificate. |
| [2305004](../errorcode-net-networkSecurity.md#2305004-failed-to-decrypt-the-certificate-signature) | Unable to decrypt certificate signature. |
| [2305006](../errorcode-net-networkSecurity.md#2305006-failed-to-decode-the-issuer-public-key) | Unable to decode issuer public key. |
| [2305007](../errorcode-net-networkSecurity.md#2305007-failed-to-sign-the-certificate) | Certificate signature failure. |
| [2305009](../errorcode-net-networkSecurity.md#2305009-invalid-certificate) | Certificate is not yet valid. |
| [2305010](../errorcode-net-networkSecurity.md#2305010-certificate-expired) | Certificate has expired. |
| [2305018](../errorcode-net-networkSecurity.md#2305018-self-signed-certificate) | Self-signed certificate. |
| [2305024](../errorcode-net-networkSecurity.md#2305024-invalid-ca) | Invalid certificate authority (CA). |
| [2305027](../errorcode-net-networkSecurity.md#2305027-untrusted-certificate) | Certificate is untrusted. |
| [2305062](../errorcode-net-networkSecurity.md#2305062-hostname-verification-failed) | Invalid hostname. |
| [2305069](../errorcode-net-networkSecurity.md#2305069-invalid-certificate-verification-context) | Invalid certificate verification context. |

**Examples**

```TypeScript
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
