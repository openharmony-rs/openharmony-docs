# IntentResult

```TypeScript
interface IntentResult<T>
```

Defines the return result of intent execution. The [generic type](../../../quick-start/introduction-to-arkts.md#generic-class-and-interface) is supported.

**Since:** 20

<!--Device-insightIntent-interface IntentResult<T>--><!--Device-insightIntent-interface IntentResult<T>-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-IntentResult-code: int--><!--Device-IntentResult-code: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## result

```TypeScript
result?: T
```

Result data returned by the intent execution, typically containing information to be passed back to the system entry point.

**Type:** T

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-IntentResult-result?: T--><!--Device-IntentResult-result?: T-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
