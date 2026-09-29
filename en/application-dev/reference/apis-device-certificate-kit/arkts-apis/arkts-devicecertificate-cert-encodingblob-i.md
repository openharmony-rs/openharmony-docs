# EncodingBlob

```TypeScript
interface EncodingBlob
```

Represents an encoded binary data block.

**Since:** 9

<!--Device-cert-interface EncodingBlob--><!--Device-cert-interface EncodingBlob-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## data

```TypeScript
data: Uint8Array
```

Encoded data.

**Type:** Uint8Array

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-EncodingBlob-data: Uint8Array--><!--Device-EncodingBlob-data: Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert

## encodingFormat

```TypeScript
encodingFormat: EncodingFormat
```

Encoding format.

**Type:** [EncodingFormat](arkts-devicecertificate-cert-encodingformat-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-EncodingBlob-encodingFormat: EncodingFormat--><!--Device-EncodingBlob-encodingFormat: EncodingFormat-End-->

**System capability:** SystemCapability.Security.Cert
