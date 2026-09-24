# MemoryLevel

```TypeScript
export enum MemoryLevel
```

Enumerates the memory levels of the entire device. You can use it in [onMemoryLevel()](arkts-ability-app-ability-ability-ability-c.md#onmemorylevel) of the UIAbility to complete different operations.

> **NOTE:** 
> 
> - The trigger conditions may differ across various devices. For example, on a standard device with 12 GB of memory:
> - When the available memory of the entire device drops to 1700 MB to 1800 MB, the **onMemoryLevel** callback with a value of **0** is triggered, indicating that the available memory is moderate.
> - When the available memory of the entire device drops to 1600 MB to 1700 MB, the **onMemoryLevel** callback with a value of **1** is triggered, indicating that the available memory is low.
> - When the available memory of the entire device drops below 1600 MB, the **onMemoryLevel** callback with a value of **2** is triggered, indicating that the available memory is critically low.
> 
> - LRU: Indicates the list sorted by the recent usage order of applications. Typically, recently used applications are placed at the head of the list (closer to the front), and the least recently used applications are placed at the tail (closer to the back). When memory is insufficient, applications closer to the tail will be cleaned up first.
> 
> - When the LRU changes, background applications will trigger the corresponding MemoryLevel (MEMORY_LEVEL_BACKGROUND_MODERATE, MEMORY_LEVEL_BACKGROUND_LOW, MEMORY_LEVEL_BACKGROUND_CRITICAL)onMemoryLevel callback based on their position in the LRU. If an application is frozen, it will receive the corresponding onMemoryLevel callback when it is awakened. Therefore, it is not recommended to perform time-consuming operations in this callback.

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

All UI elements of the application are invisible. At this point, some resources should be released. This enum only takes effect for applications that switch from the foreground to the background.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_BACKGROUND_MODERATE

```TypeScript
MEMORY_LEVEL_BACKGROUND_MODERATE = 4
```

Indicates that the application has just been used, that is, it is at the head of the Least Recently Used (LRU) list, and will not be cleaned up by the system for the time being. This enum only takes effect for background applications.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_BACKGROUND_LOW

```TypeScript
MEMORY_LEVEL_BACKGROUND_LOW = 5
```

Indicates that the application has not been used for a period of time, that is, it is in the middle of the Least Recently Used (LRU) list, and is at risk of being cleaned up by the system. This enum only takes effect for background applications.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_BACKGROUND_CRITICAL

```TypeScript
MEMORY_LEVEL_BACKGROUND_CRITICAL = 6
```

Indicates that the application has not been used for a long time, that is, it is at the tail of the Least Recently Used (LRU) list, and will be prioritized for cleanup by the system. This enum only takes effect for background applications.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
