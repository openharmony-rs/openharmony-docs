# AbilityStageContext

```TypeScript
declare class AbilityStageContext extends Context
```

The AbilityStageContext module implements the context of an ability stage. It inherits from [Context](arkts-ability-context.md). This module provides APIs for accessing a specific ability stage. You can use the APIs to obtain the ModuleInfo object and environment configuration of an ability stage.

**Inheritance/Implementation:** AbilityStageContext extends [Context](arkts-ability-context-c.md)

**Since:** 9

<!--Device-unnamed-declare class AbilityStageContext extends Context--><!--Device-unnamed-declare class AbilityStageContext extends Context-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## config

```TypeScript
config: Configuration
```

Environment variables.

**Type:** [Configuration](arkts-ability-app-ability-configuration-configuration-i.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityStageContext-config: Configuration--><!--Device-AbilityStageContext-config: Configuration-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## currentHapModuleInfo

```TypeScript
currentHapModuleInfo: HapModuleInfo
```

ModuleInfo object corresponding to the ability stage.

**Type:** [HapModuleInfo](arkts-ability-hapmoduleinfo-i.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityStageContext-currentHapModuleInfo: HapModuleInfo--><!--Device-AbilityStageContext-currentHapModuleInfo: HapModuleInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## launchElement

```TypeScript
launchElement?: ElementName
```

Indicates launch ElementName object of the abilityStage.

**Type:** [ElementName](arkts-ability-elementname-i.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AbilityStageContext-launchElement?: ElementName--><!--Device-AbilityStageContext-launchElement?: ElementName-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
