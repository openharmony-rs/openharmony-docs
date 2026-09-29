# ExecuteMode

```TypeScript
enum ExecuteMode
```

Enumerates the intent execution modes. It specifies the mode of execution passed when the intent is triggered by a system entry point. The supported execution modes for each intent are defined during intent development.

**Since:** 11

<!--Device-insightIntent-enum ExecuteMode--><!--Device-insightIntent-enum ExecuteMode-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## UI_ABILITY_FOREGROUND

```TypeScript
UI_ABILITY_FOREGROUND = 0
```

Display a UIAbility in the foreground.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExecuteMode-UI_ABILITY_FOREGROUND = 0--><!--Device-ExecuteMode-UI_ABILITY_FOREGROUND = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## UI_ABILITY_BACKGROUND

```TypeScript
UI_ABILITY_BACKGROUND = 1
```

Start a UIAbility in the background.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExecuteMode-UI_ABILITY_BACKGROUND = 1--><!--Device-ExecuteMode-UI_ABILITY_BACKGROUND = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## UI_EXTENSION_ABILITY

```TypeScript
UI_EXTENSION_ABILITY = 2
```

Start a UIExtensionAbility.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecuteMode-UI_EXTENSION_ABILITY = 2--><!--Device-ExecuteMode-UI_EXTENSION_ABILITY = 2-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
