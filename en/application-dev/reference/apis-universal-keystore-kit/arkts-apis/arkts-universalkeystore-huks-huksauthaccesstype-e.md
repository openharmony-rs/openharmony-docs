# HuksAuthAccessType

Enumerates the access control types.

**Since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_AUTH_ACCESS_INVALID_CLEAR_PASSWORD

```TypeScript
HUKS_AUTH_ACCESS_INVALID_CLEAR_PASSWORD = 1 << 0
```

The key becomes invalid after the password is cleared.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL

```TypeScript
HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL = 1 << 1
```

The key becomes invalid after a new biometric feature is added.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_AUTH_ACCESS_ALWAYS_VALID

```TypeScript
HUKS_AUTH_ACCESS_ALWAYS_VALID = 1 << 2
```

The key is always valid.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension
