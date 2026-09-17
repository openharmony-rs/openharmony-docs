# HuksKeyStorageType

Enumerates the key storage modes.

**Since:** 8

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_STORAGE_TEMP

```TypeScript
HUKS_STORAGE_TEMP = 0
```

The key is managed locally.

Note: This tag is supported since API version 8 and deprecated since API version 10. No substitute is provided because this tag is not used in key management. In key derivation scenarios, use **HUKS_STORAGE_ONLY_USED_IN_HUKS** or **HUKS_STORAGE_KEY_EXPORT_ALLOWED**.

**Since:** 8

**Deprecated since:** 10

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_STORAGE_PERSISTENT

```TypeScript
HUKS_STORAGE_PERSISTENT = 1
```

The key is managed by the HUKS service.

Note: This tag is supported since API version 8 and deprecated since API version 10. No substitute is provided because this tag is not used in key management. In key derivation scenarios, use **HUKS_STORAGE_ONLY_USED_IN_HUKS** or **HUKS_STORAGE_KEY_EXPORT_ALLOWED**.

**Since:** 8

**Deprecated since:** 10

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_STORAGE_ONLY_USED_IN_HUKS

```TypeScript
HUKS_STORAGE_ONLY_USED_IN_HUKS = 2
```

The key derived from the master key is stored in the HUKS and managed by the HUKS.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 10 to 11: SystemCapability.Security.Huks.Extension

## HUKS_STORAGE_KEY_EXPORT_ALLOWED

```TypeScript
HUKS_STORAGE_KEY_EXPORT_ALLOWED = 3
```

The key derived from the master key is exported to the service, and not managed by the HUKS.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 10 to 11: SystemCapability.Security.Huks.Extension
