# CsrGenerationConfig

```TypeScript
interface CsrGenerationConfig
```

Describes the configuration parameters for generating a CSR, including the subject name, extension, message digest (MD) algorithm, and output format.

> **NOTE:** 
> 
> - **subject** is an object of the Name type defined by X509.
> 
> - **mdName** specifies the message digest algorithm. Currently, SHA-1, SHA-256, SHA-384, and SHA-512 are supported.
> 
> - **attributes** is optional. You can specify the extension types and values defined in OpenSSL to generate a CSR, for example, **challengePassword** and **keyUsage**.
> 
> - **outFormat** specifies the format of the CSR generated. If it is not specified, the PEM format is used by default.

**Since:** 18

<!--Device-cert-interface CsrGenerationConfig--><!--Device-cert-interface CsrGenerationConfig-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## attributes

```TypeScript
attributes?: Array<CsrAttribute>
```

Extension.

**Type:** Array&lt;[CsrAttribute](arkts-devicecertificate-cert-csrattribute-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CsrGenerationConfig-attributes?: Array<CsrAttribute>--><!--Device-CsrGenerationConfig-attributes?: Array<CsrAttribute>-End-->

**System capability:** SystemCapability.Security.Cert

## mdName

```TypeScript
mdName: string
```

MD algorithm name. Currently, SHA-1, SHA-256, SHA-384, and SHA-512 are supported.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CsrGenerationConfig-mdName: string--><!--Device-CsrGenerationConfig-mdName: string-End-->

**System capability:** SystemCapability.Security.Cert

## outFormat

```TypeScript
outFormat?: EncodingBaseFormat
```

Output type. The default value is **PEM**.

**Type:** [EncodingBaseFormat](arkts-devicecertificate-cert-encodingbaseformat-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CsrGenerationConfig-outFormat?: EncodingBaseFormat--><!--Device-CsrGenerationConfig-outFormat?: EncodingBaseFormat-End-->

**System capability:** SystemCapability.Security.Cert

## subject

```TypeScript
subject: X500DistinguishedName
```

Subject name.

**Type:** [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CsrGenerationConfig-subject: X500DistinguishedName--><!--Device-CsrGenerationConfig-subject: X500DistinguishedName-End-->

**System capability:** SystemCapability.Security.Cert
