# AutoFillCallback

Auto fill callback.

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## Modules to Import

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

## onFailure

```TypeScript
onFailure: OnFillFailureFn
```

Called when auto fill request is failed to be handled.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Examples**

```TypeScript
See autoFillManager.requestAutoFill.
```

## onSuccess

```TypeScript
onSuccess: OnFillSuccessFn
```

Called when auto fill request is successfully handled.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Examples**

```TypeScript
See autoFillManager.requestAutoFill.
```
