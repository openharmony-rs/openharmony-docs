# HuksUnwrapSuite

Enumerates the algorithm suites for securely importing a key.

**Since:** 9

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 9 to 11: SystemCapability.Security.Huks.Extension

## HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING

```TypeScript
HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING = 1
```

Use X25519 for key agreement and then use AES-256 GCM to decrypt the key.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 9 to 11: SystemCapability.Security.Huks.Extension

## HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING

```TypeScript
HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING = 2
```

Use ECDH for key agreement and then use AES-256 GCM to decrypt the key.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 9 to 11: SystemCapability.Security.Huks.Extension

## HUKS_UNWRAP_SUITE_SM2_SM4_ECB_NOPADDING

```TypeScript
HUKS_UNWRAP_SUITE_SM2_SM4_ECB_NOPADDING = 5
```

Use the temporary SM4 key to encrypt the imported key and use the SM2 key that has been imported to HUKS to encrypt the SM4 key.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Security.Huks.Core
