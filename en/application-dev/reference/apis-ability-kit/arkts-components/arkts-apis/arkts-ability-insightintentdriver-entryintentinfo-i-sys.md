# EntryIntentInfo (System API)

Describes the parameters supported by the [@InsightIntentForm](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform) decorator, such as the widget name. It also describes the widget information bound to the [intent developed using a configuration file](../../../application-models/insight-intent-config-development.md).

**Since:** 20

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

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
