# GeneralName

```TypeScript
interface GeneralName
```

Represents an X.509 general name defined in RFC 5280, which can be used in the subject alternative name and other extensions.

**Since:** 12

<!--Device-cert-interface GeneralName--><!--Device-cert-interface GeneralName-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## name

```TypeScript
name?: Uint8Array
```

Value of **GeneralName** encoded in DER format.

**Type:** Uint8Array

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GeneralName-name?: Uint8Array--><!--Device-GeneralName-name?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert

## type

```TypeScript
type: GeneralNameType
```

General name type.

**Type:** [GeneralNameType](arkts-devicecertificate-cert-generalnametype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GeneralName-type: GeneralNameType--><!--Device-GeneralName-type: GeneralNameType-End-->

**System capability:** SystemCapability.Security.Cert
