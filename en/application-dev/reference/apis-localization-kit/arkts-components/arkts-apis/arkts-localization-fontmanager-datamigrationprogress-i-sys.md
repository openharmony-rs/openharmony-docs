# DataMigrationProgress (System API)

Describes the progress information of data migration, including the progress percentage and estimated remaining time. This API is the parameter type of the `onProgress` API in the data migration callback.

**Since:** 23

**System capability:** SystemCapability.Global.FontManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## progressPercentage

```TypeScript
progressPercentage: number
```

Data migration progress percentage, which is calculated based on the number or size of migrated font files and may not increase evenly. When `progressPercentage` reaches `100`, the migration task is about to complete and the `onResult` callback is about to be invoked. The value range is [0, 100].

**Type:** number

**Since:** 23

**System capability:** SystemCapability.Global.FontManager

**System API:** This is a system API.

## timeRemaining

```TypeScript
timeRemaining: number
```

Estimated remaining time, which may vary depending on factors such as device performance, file size, and system load. The value must be a non-negative integer, with a minimum value of 0. The unit is seconds.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.Global.FontManager

**System API:** This is a system API.
