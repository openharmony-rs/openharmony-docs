# UIAbilityIntentInfo (System API)

```TypeScript
interface UIAbilityIntentInfo
```

Describes the information of the UIAbility bound to the [intent developed using a configuration file](../../../application-models/insight-intent-config-development.md).

**Since:** 23

<!--Device-insightIntentDriver-interface UIAbilityIntentInfo--><!--Device-insightIntentDriver-interface UIAbilityIntentInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## abilityName

```TypeScript
readonly abilityName: string
```

Name of the UIAbility bound to the intent.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAbilityIntentInfo-readonly abilityName: string--><!--Device-UIAbilityIntentInfo-readonly abilityName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## executeMode

```TypeScript
readonly executeMode: ExecuteModeForConfiguration[]
```

Intent execution mode.

**Type:** [ExecuteModeForConfiguration](arkts-ability-insightintentdriver-executemodeforconfiguration-e-sys.md)[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAbilityIntentInfo-readonly executeMode: ExecuteModeForConfiguration[]--><!--Device-UIAbilityIntentInfo-readonly executeMode: ExecuteModeForConfiguration[]-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
