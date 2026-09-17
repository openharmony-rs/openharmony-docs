# IntentResult

Defines the return result of intent execution. The [generic type](../../../quick-start/introduction-to-arkts.md#generic-class-and-interface) is supported.

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## code

```TypeScript
code: number
```

Error code returned by the intent execution, defined by the developer.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## result

```TypeScript
result?: T
```

Result data returned by the intent execution, typically containing information to be passed back to the system entry point.

**Type:** T

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
