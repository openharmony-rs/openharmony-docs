# SaveModeFlag

Enumerates the application state saving modes. This enum is used as an input parameter of [enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md).

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## SAVE_WITH_FILE

```TypeScript
SAVE_WITH_FILE = 0x0001
```

The application state is saved and written to the local file cache.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## SAVE_WITH_SHARED_MEMORY

```TypeScript
SAVE_WITH_SHARED_MEMORY = 0x0002
```

The application state is saved in the memory. When the application exits due to a fault, it is written to the local file cache.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
