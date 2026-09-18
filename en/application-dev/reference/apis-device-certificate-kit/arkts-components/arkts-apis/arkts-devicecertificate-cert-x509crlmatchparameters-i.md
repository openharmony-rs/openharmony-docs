# X509CRLMatchParameters

Represents the parameters used to match a certificate revocation list (CRL). If no parameter is specified, all CRLs are matched.

**Since:** 11

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## issuer

```TypeScript
issuer?: Array<Uint8Array>
```

CRL issuer, in DER format.

**Type:** Array&lt;Uint8Array&gt;

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## maxCRL

```TypeScript
maxCRL?: bigint
```

Maximum value of the CRL number.

**Type:** bigint

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## minCRL

```TypeScript
minCRL?: bigint
```

Minimum value of the CRL number.

**Type:** bigint

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## updateDateTime

```TypeScript
updateDateTime?: string
```

CRL update time.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## x509Cert

```TypeScript
x509Cert?: X509Cert
```

Certificate object.

**Type:** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert
