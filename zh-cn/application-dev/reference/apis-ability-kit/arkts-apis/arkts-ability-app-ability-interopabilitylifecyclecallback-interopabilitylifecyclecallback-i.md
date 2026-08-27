# InteropAbilityLifecycleCallback

互操作Ability生命周期回调，用于监听Ability的生命周期状态变化。

**起始版本：** 23

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## 导入模块

```TypeScript
import { InteropAbilityLifecycleCallback } from '@kit.AbilityKit';
```

## onAbilityBackground

```TypeScript
onAbilityBackground: AbilityCallbackFn
```

Ability状态切换至后台时，触发该回调函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityContinue

```TypeScript
onAbilityContinue?: AbilityCallbackFn
```

Ability准备迁移时，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityCreate

```TypeScript
onAbilityCreate: AbilityCallbackFn
```

Ability被创建时，触发该回调函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityDestroy

```TypeScript
onAbilityDestroy: AbilityCallbackFn
```

Ability被销毁时，触发该回调函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityForeground

```TypeScript
onAbilityForeground: AbilityCallbackFn
```

Ability状态切换至前台时，触发该回调函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilitySaveState

```TypeScript
onAbilitySaveState?: AbilityCallbackFn
```

Ability调用onSaveState后，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillBackground

```TypeScript
onAbilityWillBackground?: AbilityCallbackFn
```

Ability状态切换至后台前，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillContinue

```TypeScript
onAbilityWillContinue?: AbilityCallbackFn
```

Ability准备调用onContinue时，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillCreate

```TypeScript
onAbilityWillCreate?: AbilityCallbackFn
```

Ability被创建前，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillDestroy

```TypeScript
onAbilityWillDestroy?: AbilityCallbackFn
```

Ability被销毁前，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillForeground

```TypeScript
onAbilityWillForeground?: AbilityCallbackFn
```

Ability状态切换至前台前，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillSaveState

```TypeScript
onAbilityWillSaveState?: AbilityCallbackFn
```

Ability准备调用onSaveState时，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onNewWant

```TypeScript
onNewWant?: AbilityCallbackFn
```

UIAbility调用onNewWant后，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWillNewWant

```TypeScript
onWillNewWant?: AbilityCallbackFn
```

UIAbility调用onNewWant前，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageActive

```TypeScript
onWindowStageActive?: WindowStageCallbackFn
```

WindowStage获焦时，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageCreate

```TypeScript
onWindowStageCreate: WindowStageCallbackFn
```

WindowStage被创建时，触发该回调函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy: WindowStageCallbackFn
```

WindowStage被销毁时，触发该回调函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageInactive

```TypeScript
onWindowStageInactive?: WindowStageCallbackFn
```

WindowStage失焦时，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageRestore

```TypeScript
onWindowStageRestore?: WindowStageCallbackFn
```

Ability调用onWindowStageRestore后，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillCreate

```TypeScript
onWindowStageWillCreate?: WindowStageCallbackFn
```

WindowStage被创建前，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillDestroy

```TypeScript
onWindowStageWillDestroy?: WindowStageCallbackFn
```

WindowStage被销毁前，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillRestore

```TypeScript
onWindowStageWillRestore?: WindowStageCallbackFn
```

Ability调用onWindowStageWillRestore后，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore
