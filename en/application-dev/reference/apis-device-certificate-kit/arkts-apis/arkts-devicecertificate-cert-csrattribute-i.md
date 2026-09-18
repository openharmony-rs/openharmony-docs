# CsrAttribute

Defines the CSR attribute representation.

<br>CSR attribute field. Currently, only string-type attribute fields are supported. The attribute value added to the CSR is encoded in UTF-8 format. The common type is challengePassword.

**Since:** 18

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## type

```TypeScript
type: string
```

Attribute type defined in PKCS #9.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert

## value

```TypeScript
value: string
```

Attribute value.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert
