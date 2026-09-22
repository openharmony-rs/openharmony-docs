# CsrGenerationConfig

```TypeScript
interface CsrGenerationConfig
```

Configuration parameters for generating a CSR, including the subject name, digest algorithm, attribute, and output format.

> **NOTE:** 
> 
> - subject is an X500DistinguishedName object.
> 
> - mdName indicates the digest algorithm name. Currently, SHA1, SHA256, SHA384, and SHA512 are supported.
> 
> - attributes is an optional parameter that specifies the attribute types and attribute values specified in PKCS #9 to generate a CSR. For example, challengePassword.
> 
> - outFormat specifies the format of the output CSR. If the format is not specified, the PEM format is used by default.

**Since:** 18

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## attributes

```TypeScript
attributes?: Array<CsrAttribute>
```

A collection of attributes.

**Type:** Array&lt;[CsrAttribute](arkts-devicecertificate-cert-csrattribute-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert

## mdName

```TypeScript
mdName: string
```

Message digest algorithm name.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert

## outFormat

```TypeScript
outFormat?: EncodingBaseFormat
```

Output format.

**Type:** [EncodingBaseFormat](arkts-devicecertificate-cert-encodingbaseformat-e.md)

**Default:** EncodingBaseFormat.PEM

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert

## subject

```TypeScript
subject: X500DistinguishedName
```

Subject name.

**Type:** [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert
