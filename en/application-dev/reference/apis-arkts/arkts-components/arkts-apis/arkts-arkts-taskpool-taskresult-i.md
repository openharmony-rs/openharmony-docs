# TaskResult

Describes the supplementary information captured in **BusinessError** in the catch branch after a task in the waiting or execution phase is canceled. In other scenarios, the task result is **undefined**.

**Since:** 20

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## error

```TypeScript
error?: Error | Object
```

Error message. By default, the value is the same as the **message** field of **BusinessError**. You are advised not to change the value.

**Type:** Error &#124; Object

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

## result

```TypeScript
result?: Object
```

Task execution result. The default value is **undefined**. You are advised not to change the value.

**Type:** Object

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang
