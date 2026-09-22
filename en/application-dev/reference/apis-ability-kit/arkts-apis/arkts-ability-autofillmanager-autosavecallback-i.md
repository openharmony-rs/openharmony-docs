# AutoSaveCallback

```TypeScript
export interface AutoSaveCallback
```

Implements callbacks triggered when auto-save is complete.

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## Modules to Import

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

## onFailure

```TypeScript
onFailure(): void
```

Called when auto save request is failed to be handled.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Examples**

See autoFillManager.requestAutoSave.

## onSuccess

```TypeScript
onSuccess(): void
```

Called when auto save request is successfully handled.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Examples**

See autoFillManager.requestAutoSave.
