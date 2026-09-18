# X509TrustAnchor

Represents an X.509 trust anchor, which is used to verify the certificate chain. The certificate or public key in the trust anchor is used as the trusted root to verify the certificate chain.

**Since:** 11

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## CACert

```TypeScript
CACert?: X509Cert
```

Trusted CA certificate. If **CACert** is set, only **CACert** is used to validate the certificate chain. **CAPubKey** and **CASubject** are not used.

**Type:** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## CAPubKey

```TypeScript
CAPubKey?: Uint8Array
```

Public key of the trusted CA certificate, in DER format. This parameter takes effect only when **CACert** is not set.

**Type:** Uint8Array

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## CASubject

```TypeScript
CASubject?: Uint8Array
```

Subject of the trusted CA certificate, in DER format. This parameter takes effect only when **CAPubKey** is set. The validation object is determined based on the **CAPubKey** type (self-signed or upper-level), and can be the subject or issuer of the root certificate.

**Type:** Uint8Array

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## nameConstraints

```TypeScript
nameConstraints?: Uint8Array
```

Name constraints, in DER format. Only the leaf certificate of the current certificate chain is validated.

**Type:** Uint8Array

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert
