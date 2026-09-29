# AppPreloadType

```TypeScript
export enum AppPreloadType
```

Enumerates the preloading types of the current application process.

**Since:** 22

<!--Device-application-export enum AppPreloadType--><!--Device-application-export enum AppPreloadType-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## UNSPECIFIED

```TypeScript
UNSPECIFIED = 0
```

No preloading has taken place, or the preloaded data has been cleared.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppPreloadType-UNSPECIFIED = 0--><!--Device-AppPreloadType-UNSPECIFIED = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## TYPE_CREATE_PROCESS

```TypeScript
TYPE_CREATE_PROCESS = 1
```

Preloads the process up to the point of process creation completion.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppPreloadType-TYPE_CREATE_PROCESS = 1--><!--Device-AppPreloadType-TYPE_CREATE_PROCESS = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## TYPE_CREATE_ABILITY_STAGE

```TypeScript
TYPE_CREATE_ABILITY_STAGE = 2
```

Preloads the process up to the point of [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md) creation completion.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppPreloadType-TYPE_CREATE_ABILITY_STAGE = 2--><!--Device-AppPreloadType-TYPE_CREATE_ABILITY_STAGE = 2-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## TYPE_CREATE_WINDOW_STAGE

```TypeScript
TYPE_CREATE_WINDOW_STAGE = 3
```

Preloads the process up to the point of [WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-n.md) creation completion.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppPreloadType-TYPE_CREATE_WINDOW_STAGE = 3--><!--Device-AppPreloadType-TYPE_CREATE_WINDOW_STAGE = 3-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## TYPE_CREATE_BACKGROUND_ABILITY

```TypeScript
TYPE_CREATE_BACKGROUND_ABILITY = 4
```

Preloads the process up to the point of [onBackground](arkts-ability-app-ability-uiability-uiability-c.md#onbackground) execution completion.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppPreloadType-TYPE_CREATE_BACKGROUND_ABILITY = 4--><!--Device-AppPreloadType-TYPE_CREATE_BACKGROUND_ABILITY = 4-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
