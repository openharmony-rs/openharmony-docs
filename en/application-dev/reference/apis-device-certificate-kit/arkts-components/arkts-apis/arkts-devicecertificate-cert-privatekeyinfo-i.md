# PrivateKeyInfo

Represents the private key information.

**Since:** 18

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## key

```TypeScript
key: string | Uint8Array
```

Encrypted or unencrypted private key in PEM or DER format.

**Type:** string &#124; Uint8Array

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert

## password

```TypeScript
password?: string
```

Password of the private key, if the private key is encrypted.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert
