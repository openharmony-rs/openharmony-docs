# CmsVerificationConfig

```TypeScript
interface CmsVerificationConfig
```

Represents CMS verification configuration.

**Since:** 22

<!--Device-cert-interface CmsVerificationConfig--><!--Device-cert-interface CmsVerificationConfig-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## contentData

```TypeScript
contentData?: Uint8Array
```

Content data. If the detached mode is used, you need to specify the plaintext data. This parameter can be left empty in attached mode.

**Type:** Uint8Array

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsVerificationConfig-contentData?: Uint8Array--><!--Device-CmsVerificationConfig-contentData?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert

## contentDataFormat

```TypeScript
contentDataFormat?: CmsContentDataFormat
```

Format of the content. The default value is **CmsContentDataFormat.BINARY**.

**Type:** [CmsContentDataFormat](arkts-devicecertificate-cert-cmscontentdataformat-e.md)

**Default:** CmsContentDataFormat.BINARY

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsVerificationConfig-contentDataFormat?: CmsContentDataFormat--><!--Device-CmsVerificationConfig-contentDataFormat?: CmsContentDataFormat-End-->

**System capability:** SystemCapability.Security.Cert

## signerCerts

```TypeScript
signerCerts?: Array<X509Cert>
```

Signer certificates.

**Type:** Array&lt;[X509Cert](arkts-devicecertificate-cert-x509cert-i.md)&gt;

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsVerificationConfig-signerCerts?: Array<X509Cert>--><!--Device-CmsVerificationConfig-signerCerts?: Array<X509Cert>-End-->

**System capability:** SystemCapability.Security.Cert

## trustCerts

```TypeScript
trustCerts: Array<X509Cert>
```

Trusted certificates.

> **NOTE:** 
> 
> You need to configure the trust certificates of all signers.

**Type:** Array&lt;[X509Cert](arkts-devicecertificate-cert-x509cert-i.md)&gt;

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsVerificationConfig-trustCerts: Array<X509Cert>--><!--Device-CmsVerificationConfig-trustCerts: Array<X509Cert>-End-->

**System capability:** SystemCapability.Security.Cert
