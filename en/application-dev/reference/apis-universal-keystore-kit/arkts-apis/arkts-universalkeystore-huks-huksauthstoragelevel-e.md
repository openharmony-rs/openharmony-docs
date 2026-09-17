# HuksAuthStorageLevel

Enumerates the storage security levels of a key.

> **NOTE:** 
> 
> When using a key whose storage level is ECE, you are advised to clear the session resources created using the key
> by detecting the
> [lock screen event](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_screen_locked)
> to ensure security.

**Since:** 11

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API version 11: SystemCapability.Security.Huks.Extension

## HUKS_AUTH_STORAGE_LEVEL_DE

```TypeScript
HUKS_AUTH_STORAGE_LEVEL_DE = 0
```

The key can be accessed only after the device is started.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API version 11: SystemCapability.Security.Huks.Extension

## HUKS_AUTH_STORAGE_LEVEL_CE

```TypeScript
HUKS_AUTH_STORAGE_LEVEL_CE = 1
```

The key can be accessed only after the first unlock of the device.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API version 11: SystemCapability.Security.Huks.Extension

## HUKS_AUTH_STORAGE_LEVEL_ECE

```TypeScript
HUKS_AUTH_STORAGE_LEVEL_ECE = 2
```

The key can be accessed only when the device is unlocked.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API version 11: SystemCapability.Security.Huks.Extension
