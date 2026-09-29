# CmsKeyAgreeRecipientInfo

```TypeScript
interface CmsKeyAgreeRecipientInfo
```

Represents KeyAgree recipient information for CMS enveloped data.

**Since:** 22

<!--Device-cert-interface CmsKeyAgreeRecipientInfo--><!--Device-cert-interface CmsKeyAgreeRecipientInfo-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## cert

```TypeScript
cert: X509Cert
```

EC certificate.

**Type:** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsKeyAgreeRecipientInfo-cert: X509Cert--><!--Device-CmsKeyAgreeRecipientInfo-cert: X509Cert-End-->

**System capability:** SystemCapability.Security.Cert

## digestAlgorithm

```TypeScript
digestAlgorithm?: CmsKeyAgreeRecipientDigestAlgorithm
```

KDF digest algorithm. The default value is **SHA256**.

**Type:** [CmsKeyAgreeRecipientDigestAlgorithm](arkts-devicecertificate-cert-cmskeyagreerecipientdigestalgorithm-e.md)

**Default:** CmsKeyAgreeRecipientDigestAlgorithm.SHA256

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsKeyAgreeRecipientInfo-digestAlgorithm?: CmsKeyAgreeRecipientDigestAlgorithm--><!--Device-CmsKeyAgreeRecipientInfo-digestAlgorithm?: CmsKeyAgreeRecipientDigestAlgorithm-End-->

**System capability:** SystemCapability.Security.Cert
