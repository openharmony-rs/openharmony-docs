# EntryIntentDecoratorInfo

Inherits from [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md) and is used to describe the parameters supported by the [@InsightIntentEntry](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententry) decorator.

**Inheritance/Implementation:** EntryIntentDecoratorInfo extends [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentLink, InsightIntentPage, InsightIntentFunctionMethod, InsightIntentFunction, InsightIntentEntry, LinkParamCategory, InsightIntentForm, InsightIntentEntity } from '@kit.AbilityKit';
```

## abilityName

```TypeScript
abilityName: string
```

Name of the ability bound to the intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## executeMode

```TypeScript
executeMode: insightIntent.ExecuteMode[]
```

Execution mode of the intent call, that is, execution mode supported when the bound ability is started.

**Type:** [insightIntent.ExecuteMode](arkts-ability-insightintent-executemode-e.md)[]

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
