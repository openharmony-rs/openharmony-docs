# CmsEnvelopedDecryptionConfig

```TypeScript
interface CmsEnvelopedDecryptionConfig
```

Configuration used for decrypting CMS enveloped data.

**Since:** 22

<!--Device-cert-interface CmsEnvelopedDecryptionConfig--><!--Device-cert-interface CmsEnvelopedDecryptionConfig-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## cert

```TypeScript
cert?: X509Cert
```

Public key certificate. This parameter is left empty by default.

**Type:** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsEnvelopedDecryptionConfig-cert?: X509Cert--><!--Device-CmsEnvelopedDecryptionConfig-cert?: X509Cert-End-->

**System capability:** SystemCapability.Security.Cert

## contentDataFormat

```TypeScript
contentDataFormat?: CmsContentDataFormat
```

Format of the content.

**Type:** [CmsContentDataFormat](arkts-devicecertificate-cert-cmscontentdataformat-e.md)

**Default:** CmsContentDataFormat.BINARY

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsEnvelopedDecryptionConfig-contentDataFormat?: CmsContentDataFormat--><!--Device-CmsEnvelopedDecryptionConfig-contentDataFormat?: CmsContentDataFormat-End-->

**System capability:** SystemCapability.Security.Cert

## encryptedContentData

```TypeScript
encryptedContentData?: Uint8Array
```

Encrypted content data for detached CMS enveloped data, used when the CMS structure does not contain the encrypted content inline.

**Type:** Uint8Array

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsEnvelopedDecryptionConfig-encryptedContentData?: Uint8Array--><!--Device-CmsEnvelopedDecryptionConfig-encryptedContentData?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert

## keyInfo

```TypeScript
keyInfo?: PrivateKeyInfo
```

Private key parameter. This parameter is left empty by default.

**Type:** [PrivateKeyInfo](arkts-devicecertificate-cert-privatekeyinfo-i.md)

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsEnvelopedDecryptionConfig-keyInfo?: PrivateKeyInfo--><!--Device-CmsEnvelopedDecryptionConfig-keyInfo?: PrivateKeyInfo-End-->

**System capability:** SystemCapability.Security.Cert
