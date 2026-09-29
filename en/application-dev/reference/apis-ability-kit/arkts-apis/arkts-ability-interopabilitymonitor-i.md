# InteropAbilityMonitor

```TypeScript
export interface InteropAbilityMonitor
```

Provide methods for matching monitored Ability objects that meet specified conditions. The most recently matched Ability objects will be saved in the InteropAbilityMonitor object.

**Since:** 26.0.0

<!--Device-unnamed-export interface InteropAbilityMonitor--><!--Device-unnamed-export interface InteropAbilityMonitor-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityBackground

```TypeScript
onAbilityBackground?: AbilityCallbackFn
```

Called back when the state of the ability changes to background.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-InteropAbilityMonitor-onAbilityBackground?: AbilityCallbackFn--><!--Device-InteropAbilityMonitor-onAbilityBackground?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityCreate

```TypeScript
onAbilityCreate?: AbilityCallbackFn
```

Called back when the ability is created.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-InteropAbilityMonitor-onAbilityCreate?: AbilityCallbackFn--><!--Device-InteropAbilityMonitor-onAbilityCreate?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityDestroy

```TypeScript
onAbilityDestroy?: AbilityCallbackFn
```

Called back before the ability is destroyed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-InteropAbilityMonitor-onAbilityDestroy?: AbilityCallbackFn--><!--Device-InteropAbilityMonitor-onAbilityDestroy?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityForeground

```TypeScript
onAbilityForeground?: AbilityCallbackFn
```

Called back when the state of the ability changes to foreground.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-InteropAbilityMonitor-onAbilityForeground?: AbilityCallbackFn--><!--Device-InteropAbilityMonitor-onAbilityForeground?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onWindowStageCreate

```TypeScript
onWindowStageCreate?: AbilityCallbackFn
```

Called back when an ability window stage is created.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-InteropAbilityMonitor-onWindowStageCreate?: AbilityCallbackFn--><!--Device-InteropAbilityMonitor-onWindowStageCreate?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy?: AbilityCallbackFn
```

Called back when an ability window stage is destroyed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-InteropAbilityMonitor-onWindowStageDestroy?: AbilityCallbackFn--><!--Device-InteropAbilityMonitor-onWindowStageDestroy?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onWindowStageRestore

```TypeScript
onWindowStageRestore?: AbilityCallbackFn
```

Called back when an ability window stage is restored.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-InteropAbilityMonitor-onWindowStageRestore?: AbilityCallbackFn--><!--Device-InteropAbilityMonitor-onWindowStageRestore?: AbilityCallbackFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## abilityName

```TypeScript
abilityName: string
```

The name of the ability to monitor.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-InteropAbilityMonitor-abilityName: string--><!--Device-InteropAbilityMonitor-abilityName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## moduleName

```TypeScript
moduleName?: string
```

The name of the module to monitor.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-InteropAbilityMonitor-moduleName?: string--><!--Device-InteropAbilityMonitor-moduleName?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
