# X509CertRevokedParams

Parameters for checking certificate revocation status.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## allowDownloadCrl

```TypeScript
allowDownloadCrl?: boolean
```

Indicates whether to allow CRL download. The default value is false. true: The CDP extension of the certificate is used to download the CRL. false: Do not attempt to download the CRL.

> **NOTE:** 
> 
> Skip download if matching CRL exists in crls.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## allowOcspCheckOnline

```TypeScript
allowOcspCheckOnline?: boolean
```

Indicates whether to allow online OCSP check. The default value is false.  
- **true**: performs online OCSP check, that is, attempts to obtain the OCSP URL from the AIA extension of the  
certificate and send a request to obtain a response;  
- **false**: does not perform online OCSP check.

> **NOTE:** 
> 
> Skip online OCSP check if a matching OCSP response is found in ocspResponses.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## crls

```TypeScript
crls?: Array<X509CRL>
```

CRL list. Maximum count: 100.

**Type:** Array&lt;[X509CRL](arkts-devicecertificate-cert-x509crl-i.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## ocspDigest

```TypeScript
ocspDigest?: OcspDigest
```

Digest algorithm used by OCSP requests. The default value is SHA256.

**Type:** [OcspDigest](arkts-devicecertificate-cert-ocspdigest-e.md)

**Default:** SHA256

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## ocspResponses

```TypeScript
ocspResponses?: Array<Uint8Array>
```

Preconfigured OCSP response data. Maximum count: 100.

**Type:** Array&lt;Uint8Array&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## revocationFlags

```TypeScript
revocationFlags: Array<CertRevocationFlag>
```

Revocation check flag. Array length range: [1,4]. The array must contain either CERT_REVOCATION_CRL_CHECK or CERT_REVOCATION_OCSP_CHECK.

**Type:** Array&lt;[CertRevocationFlag](arkts-devicecertificate-cert-certrevocationflag-e.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert
