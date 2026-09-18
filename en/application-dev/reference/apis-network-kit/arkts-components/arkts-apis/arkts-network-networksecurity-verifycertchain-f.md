# verifyCertChain

## Modules to Import

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
```

## verifyCertChain

```TypeScript
export function verifyCertChain(cert: CertBlob[], caCert?: CertBlob, hostname?: string): Promise<CertBlob[]>
```

Verifies the server certificate chain and returns a sorted chain.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cert | [CertBlob](arkts-network-networksecurity-certblob-i.md)[] | Yes | Certificate chain to be verified. |
| caCert | [CertBlob](arkts-network-networksecurity-certblob-i.md) | No | Incoming custom CA cert. |
| hostname | string | No | Hostname to be verified. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CertBlob](arkts-network-networksecurity-certblob-i.md)[]&gt; | Returns a promise that resolves to the sorted certificate chain (ordered from leaf to root) if verification succeeds. |

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
| 2305062 | Invalid hostname. |
| [2305069](../errorcode-net-networkSecurity.md#2305069-invalid-certificate-verification-context) | Invalid certificate verification context. |
