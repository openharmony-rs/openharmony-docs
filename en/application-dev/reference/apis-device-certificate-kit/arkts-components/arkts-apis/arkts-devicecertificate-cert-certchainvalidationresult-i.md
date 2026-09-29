# CertChainValidationResult

```TypeScript
interface CertChainValidationResult
```

Represents the return value of certificate chain validation.

**Since:** 11

<!--Device-cert-interface CertChainValidationResult--><!--Device-cert-interface CertChainValidationResult-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## entityCert

```TypeScript
readonly entityCert: X509Cert
```

Entity certificate.

**Type:** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertChainValidationResult-readonly entityCert: X509Cert--><!--Device-CertChainValidationResult-readonly entityCert: X509Cert-End-->

**System capability:** SystemCapability.Security.Cert

## trustAnchor

```TypeScript
readonly trustAnchor: X509TrustAnchor
```

Trust anchor.

**Type:** [X509TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md)

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertChainValidationResult-readonly trustAnchor: X509TrustAnchor--><!--Device-CertChainValidationResult-readonly trustAnchor: X509TrustAnchor-End-->

**System capability:** SystemCapability.Security.Cert
