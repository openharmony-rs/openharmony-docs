# HuksKeyPurpose

Enumerates the key purposes.

A key can be used only for a single purpose. You cannot use the same key for both encryption/decryption and signature verification.

**Since:** 8

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_KEY_PURPOSE_ENCRYPT

```TypeScript
HUKS_KEY_PURPOSE_ENCRYPT = 1
```

Used to encrypt the plaintext.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_KEY_PURPOSE_DECRYPT

```TypeScript
HUKS_KEY_PURPOSE_DECRYPT = 2
```

Used to decrypt the cipher text.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_KEY_PURPOSE_SIGN

```TypeScript
HUKS_KEY_PURPOSE_SIGN = 4
```

Used for signing.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_VERIFY

```TypeScript
HUKS_KEY_PURPOSE_VERIFY = 8
```

Used to verify the signature.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_DERIVE

```TypeScript
HUKS_KEY_PURPOSE_DERIVE = 16
```

Used to derive a key.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_WRAP

```TypeScript
HUKS_KEY_PURPOSE_WRAP = 32
```

Used for an encrypted export.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_UNWRAP

```TypeScript
HUKS_KEY_PURPOSE_UNWRAP = 64
```

Used for a secure import.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_MAC

```TypeScript
HUKS_KEY_PURPOSE_MAC = 128
```

Used to generate a message authentication code.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_AGREE

```TypeScript
HUKS_KEY_PURPOSE_AGREE = 256
```

Used for key agreement.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension
