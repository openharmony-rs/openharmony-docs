# MemoryLevel

Enumerates the memory levels of the entire device. You can use it in [onMemoryLevel()](arkts-ability-app-ability-ability-ability-c.md#onmemorylevel) of the UIAbility to complete different operations.

> **NOTE:** 
> 
> - The trigger conditions may differ across various devices. For example, on a standard device with 12 GB of memory:
> - When the available memory of the entire device drops to 1700 MB to 1800 MB, the **onMemoryLevel** callback with a value of **0** is triggered, indicating that the available memory is moderate.
> - When the available memory of the entire device drops to 1600 MB to 1700 MB, the **onMemoryLevel** callback with a value of **1** is triggered, indicating that the available memory is low.
> - When the available memory of the entire device drops below 1600 MB, the **onMemoryLevel** callback with a value of **2** is triggered, indicating that the available memory is critically low.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_MODERATE

```TypeScript
MEMORY_LEVEL_MODERATE = 0
```

Indicates that the system has a moderate amount of available memory. Due to differences in system-wide memory thresholds across devices, the actual performance may vary by product. For details, please refer to the notes below.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_LOW

```TypeScript
MEMORY_LEVEL_LOW = 1
```

Indicates that the system has low available memory. Due to differences in system-wide memory thresholds across devices, the actual performance may vary by product. For details, please refer to the notes below.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_CRITICAL

```TypeScript
MEMORY_LEVEL_CRITICAL = 2
```

Indicates that the system has critically low available memory. Due to differences in system-wide memory thresholds across devices, the actual performance may vary by product. For details, please refer to the notes below.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_UI_HIDDEN

```TypeScript
MEMORY_LEVEL_UI_HIDDEN = 3
```

All UI elements of the process are hidden.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_BACKGROUND_MODERATE

```TypeScript
MEMORY_LEVEL_BACKGROUND_MODERATE = 4
```

The process is in the background and the available memory of the entire device is moderate.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_BACKGROUND_LOW

```TypeScript
MEMORY_LEVEL_BACKGROUND_LOW = 5
```

The process is in the background and the available memory of the entire device is low.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_BACKGROUND_CRITICAL

```TypeScript
MEMORY_LEVEL_BACKGROUND_CRITICAL = 6
```

The process is in the background and the available memory of the entire device is extremely low.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
