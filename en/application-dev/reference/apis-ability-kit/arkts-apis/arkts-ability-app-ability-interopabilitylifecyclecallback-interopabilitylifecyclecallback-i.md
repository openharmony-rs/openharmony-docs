# InteropAbilityLifecycleCallback

The interop ability lifecycle callback.

@typedef InteropAbilityLifecycleCallback

**Since:** 23

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## Modules to Import

```TypeScript
import { InteropAbilityLifecycleCallback } from '@kit.AbilityKit';
```

## onAbilityBackground

```TypeScript
onAbilityBackground: AbilityCallbackFn
```

Called back when the state of an ability changes to background.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityContinue

```TypeScript
onAbilityContinue?: AbilityCallbackFn
```

Called back when an ability prepares to continue.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityCreate

```TypeScript
onAbilityCreate: AbilityCallbackFn
```

Called back when an ability is started for initialization.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityDestroy

```TypeScript
onAbilityDestroy: AbilityCallbackFn
```

Called back when an ability is destroyed.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityForeground

```TypeScript
onAbilityForeground: AbilityCallbackFn
```

Called back when the state of an ability changes to foreground.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilitySaveState

```TypeScript
onAbilitySaveState?: AbilityCallbackFn
```

Called back when the ability has called onSaveState.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillBackground

```TypeScript
onAbilityWillBackground?: AbilityCallbackFn
```

Called back before the state of an ability changes to background.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillContinue

```TypeScript
onAbilityWillContinue?: AbilityCallbackFn
```

Called back when the ability prepares to call onContinue.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillCreate

```TypeScript
onAbilityWillCreate?: AbilityCallbackFn
```

Called back before an ability is started for initialization.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillDestroy

```TypeScript
onAbilityWillDestroy?: AbilityCallbackFn
```

Called back before an ability is destroyed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillForeground

```TypeScript
onAbilityWillForeground?: AbilityCallbackFn
```

Called back before the state of an ability changes to foreground.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillSaveState

```TypeScript
onAbilityWillSaveState?: AbilityCallbackFn
```

Called back when the ability prepares to call onSaveState.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onNewWant

```TypeScript
onNewWant?: AbilityCallbackFn
```

Called back after the UIAbility called onNewWant.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWillNewWant

```TypeScript
onWillNewWant?: AbilityCallbackFn
```

Called back before the UIAbility will called onNewWant.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageActive

```TypeScript
onWindowStageActive?: WindowStageCallbackFn
```

Called back when a window stage is active.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageCreate

```TypeScript
onWindowStageCreate: WindowStageCallbackFn
```

Called back when a window stage is created.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy: WindowStageCallbackFn
```

Called back when a window stage is destroyed.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageInactive

```TypeScript
onWindowStageInactive?: WindowStageCallbackFn
```

Called back when a window stage is inactive.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageRestore

```TypeScript
onWindowStageRestore?: WindowStageCallbackFn
```

Called back when the ability has called onWindowStageRestore.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillCreate

```TypeScript
onWindowStageWillCreate?: WindowStageCallbackFn
```

Called back before a window stage is created.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillDestroy

```TypeScript
onWindowStageWillDestroy?: WindowStageCallbackFn
```

Called back before a window stage is destroyed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillRestore

```TypeScript
onWindowStageWillRestore?: WindowStageCallbackFn
```

Called back when the ability has called onWindowStageWillRestore.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore
