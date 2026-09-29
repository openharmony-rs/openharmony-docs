# CmsSignerConfig

```TypeScript
interface CmsSignerConfig
```

Represents the configuration of the CMS signer.

**Since:** 18

<!--Device-cert-interface CmsSignerConfig--><!--Device-cert-interface CmsSignerConfig-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## addAttr

```TypeScript
addAttr?: boolean
```

Whether to add the signature attribute. The default value is **true**. **true**: yes; **false**: no.

**Type:** boolean

**Default:** true

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-CmsSignerConfig-addAttr?: boolean--><!--Device-CmsSignerConfig-addAttr?: boolean-End-->

**System capability:** SystemCapability.Security.Cert

## addCert

```TypeScript
addCert?: boolean
```

Whether to add a certificate. The default value is **true**. **true**: yes; **false**: no.

**Type:** boolean

**Default:** true

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-CmsSignerConfig-addCert?: boolean--><!--Device-CmsSignerConfig-addCert?: boolean-End-->

**System capability:** SystemCapability.Security.Cert

## addSmimeCapAttr

```TypeScript
addSmimeCapAttr?: boolean
```

Whether to add the SMIME capability to the CMS object. The default value is **true**. **true**: yes; **false**: no.

**Type:** boolean

**Default:** true

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-CmsSignerConfig-addSmimeCapAttr?: boolean--><!--Device-CmsSignerConfig-addSmimeCapAttr?: boolean-End-->

**System capability:** SystemCapability.Security.Cert

## mdName

```TypeScript
mdName: string
```

Message digest algorithm, for example, **SHA384**. Currently, **SHA1**, **SHA256**, **SHA384**, and **SHA512** are supported.

**Type:** string

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-CmsSignerConfig-mdName: string--><!--Device-CmsSignerConfig-mdName: string-End-->

**System capability:** SystemCapability.Security.Cert

## rsaSignaturePadding

```TypeScript
rsaSignaturePadding?: CmsRsaSignaturePadding
```

Padding mode for an RSA signature. The default value is **PKCS1_PADDING**. <br>When **PKCS1_PSS_PADDING** is set, **mdName** must be set to **SHA256**, **SHA384**, or **SHA512**.

> **NOTE:** 
> 
> This parameter is valid only when the private key type of the signature is RSA.

**Type:** [CmsRsaSignaturePadding](arkts-devicecertificate-cert-cmsrsasignaturepadding-e.md)

**Default:** CmsRsaSignaturePadding.PKCS1_PADDING

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsSignerConfig-rsaSignaturePadding?: CmsRsaSignaturePadding--><!--Device-CmsSignerConfig-rsaSignaturePadding?: CmsRsaSignaturePadding-End-->

**System capability:** SystemCapability.Security.Cert
