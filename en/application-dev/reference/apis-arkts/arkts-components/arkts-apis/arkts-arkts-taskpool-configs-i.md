# Configs

Defines the task configs interface

**Since:** 24

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## priority

```TypeScript
priority?: Priority
```

The priority of the task. The default value is taskpool.Priority.MEDIUM.

**Type:** [Priority](arkts-arkts-taskpool-priority-e.md)

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Utils.Lang

## timeout

```TypeScript
timeout?: number
```

The timeout for the task in ms. Suggest passing in integers. If decimals are passed in, they will be rounded down. If this parameter is omitted, timeout will take the default value of 0 and no timeout logic will be executed. **NOTE:** 
1. The timeout period is not a precise time, and the actual timeout period may differ from the expected time.
2. If the value is less than 1, it will be defaulted to **0**.
3. The value is subject to system limitations. If it exceeds 2^31 �C 1, the value will be **0**.

**Type:** number

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Utils.Lang
