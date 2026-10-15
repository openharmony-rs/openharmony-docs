# EntryIntentInfo (System API)

```TypeScript
interface EntryIntentInfo
```

Describes the parameters supported by the [@InsightIntentEntry](arkts-ability-app-ability-insightintentdecorator-insightintententry-d.md#insightintententry) decorator, such as the intent execution mode.

**Since:** 20

<!--Device-insightIntentDriver-interface EntryIntentInfo--><!--Device-insightIntentDriver-interface EntryIntentInfo-End-->

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

Ability name.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-EntryIntentInfo-readonly abilityName: string--><!--Device-EntryIntentInfo-readonly abilityName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## executeMode

```TypeScript
readonly executeMode: insightIntent.ExecuteMode[]
```

Intent execution mode. that is, execution mode supported when the bound ability is started.

**Type:** [insightIntent.ExecuteMode](arkts-ability-insightintent-executemode-e.md)[]

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-EntryIntentInfo-readonly executeMode: insightIntent.ExecuteMode[]--><!--Device-EntryIntentInfo-readonly executeMode: insightIntent.ExecuteMode[]-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
