# CertValidationResult

```TypeScript
interface CertValidationResult
```

Represents the certificate verification result.

**Since:** 26.0.0

<!--Device-cert-interface CertValidationResult--><!--Device-cert-interface CertValidationResult-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## certChain

```TypeScript
readonly certChain: Array<X509Cert>
```

Verified certificate chain. When the verification is successful, a complete certificate chain (from the end-entity certificate to the trust anchor) is returned. It can be used for subsequent certificate information query or other verification operations.

**Type:** Array&lt;[X509Cert](arkts-devicecertificate-cert-x509cert-i.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertValidationResult-readonly certChain: Array<X509Cert>--><!--Device-CertValidationResult-readonly certChain: Array<X509Cert>-End-->

**System capability:** SystemCapability.Security.Cert
