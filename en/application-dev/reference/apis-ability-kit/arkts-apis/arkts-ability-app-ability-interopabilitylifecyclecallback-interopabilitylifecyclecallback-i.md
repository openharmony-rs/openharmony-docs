# InteropAbilityLifecycleCallback

```TypeScript
declare interface InteropAbilityLifecycleCallback
```

The interop ability lifecycle callback.

@typedef InteropAbilityLifecycleCallback

**Since:** 23

<!--Device-unnamed-declare interface InteropAbilityLifecycleCallback--><!--Device-unnamed-declare interface InteropAbilityLifecycleCallback-End-->

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

<!--Device-InteropAbilityLifecycleCallback-onAbilityBackground: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilityBackground: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityContinue

```TypeScript
onAbilityContinue?: AbilityCallbackFn
```

Called back when an ability prepares to continue.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onAbilityContinue?: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilityContinue?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityCreate

```TypeScript
onAbilityCreate: AbilityCallbackFn
```

Called back when an ability is started for initialization.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onAbilityCreate: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilityCreate: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityDestroy

```TypeScript
onAbilityDestroy: AbilityCallbackFn
```

Called back when an ability is destroyed.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onAbilityDestroy: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilityDestroy: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityForeground

```TypeScript
onAbilityForeground: AbilityCallbackFn
```

Called back when the state of an ability changes to foreground.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onAbilityForeground: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilityForeground: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilitySaveState

```TypeScript
onAbilitySaveState?: AbilityCallbackFn
```

Called back when the ability has called onSaveState.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onAbilitySaveState?: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilitySaveState?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillBackground

```TypeScript
onAbilityWillBackground?: AbilityCallbackFn
```

Called back before the state of an ability changes to background.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onAbilityWillBackground?: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilityWillBackground?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillContinue

```TypeScript
onAbilityWillContinue?: AbilityCallbackFn
```

Called back when the ability prepares to call onContinue.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onAbilityWillContinue?: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilityWillContinue?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillCreate

```TypeScript
onAbilityWillCreate?: AbilityCallbackFn
```

Called back before an ability is started for initialization.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onAbilityWillCreate?: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilityWillCreate?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillDestroy

```TypeScript
onAbilityWillDestroy?: AbilityCallbackFn
```

Called back before an ability is destroyed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onAbilityWillDestroy?: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilityWillDestroy?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillForeground

```TypeScript
onAbilityWillForeground?: AbilityCallbackFn
```

Called back before the state of an ability changes to foreground.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onAbilityWillForeground?: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilityWillForeground?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillSaveState

```TypeScript
onAbilityWillSaveState?: AbilityCallbackFn
```

Called back when the ability prepares to call onSaveState.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onAbilityWillSaveState?: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onAbilityWillSaveState?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onNewWant

```TypeScript
onNewWant?: AbilityCallbackFn
```

Called back after the UIAbility called onNewWant.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onNewWant?: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onNewWant?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWillNewWant

```TypeScript
onWillNewWant?: AbilityCallbackFn
```

Called back before the UIAbility will called onNewWant.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onWillNewWant?: AbilityCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onWillNewWant?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageActive

```TypeScript
onWindowStageActive?: WindowStageCallbackFn
```

Called back when a window stage is active.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onWindowStageActive?: WindowStageCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onWindowStageActive?: WindowStageCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageCreate

```TypeScript
onWindowStageCreate: WindowStageCallbackFn
```

Called back when a window stage is created.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onWindowStageCreate: WindowStageCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onWindowStageCreate: WindowStageCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy: WindowStageCallbackFn
```

Called back when a window stage is destroyed.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onWindowStageDestroy: WindowStageCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onWindowStageDestroy: WindowStageCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageInactive

```TypeScript
onWindowStageInactive?: WindowStageCallbackFn
```

Called back when a window stage is inactive.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onWindowStageInactive?: WindowStageCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onWindowStageInactive?: WindowStageCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageRestore

```TypeScript
onWindowStageRestore?: WindowStageCallbackFn
```

Called back when the ability has called onWindowStageRestore.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onWindowStageRestore?: WindowStageCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onWindowStageRestore?: WindowStageCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillCreate

```TypeScript
onWindowStageWillCreate?: WindowStageCallbackFn
```

Called back before a window stage is created.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onWindowStageWillCreate?: WindowStageCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onWindowStageWillCreate?: WindowStageCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillDestroy

```TypeScript
onWindowStageWillDestroy?: WindowStageCallbackFn
```

Called back before a window stage is destroyed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onWindowStageWillDestroy?: WindowStageCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onWindowStageWillDestroy?: WindowStageCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillRestore

```TypeScript
onWindowStageWillRestore?: WindowStageCallbackFn
```

Called back when the ability has called onWindowStageWillRestore.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InteropAbilityLifecycleCallback-onWindowStageWillRestore?: WindowStageCallbackFn--><!--Device-InteropAbilityLifecycleCallback-onWindowStageWillRestore?: WindowStageCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore
