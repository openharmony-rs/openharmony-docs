# CsrAttribute

```TypeScript
interface CsrAttribute
```

Defines the CSR attribute.

<br>The CSR attribute field can only be set to a UTF-8 string currently. **type** is commonly set to **challengePassword**.

**Since:** 18

<!--Device-cert-interface CsrAttribute--><!--Device-cert-interface CsrAttribute-End-->

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

<!--Device-CsrAttribute-type: string--><!--Device-CsrAttribute-type: string-End-->

**System capability:** SystemCapability.Security.Cert

## value

```TypeScript
value: string
```

Attribute value.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CsrAttribute-value: string--><!--Device-CsrAttribute-value: string-End-->

**System capability:** SystemCapability.Security.Cert
