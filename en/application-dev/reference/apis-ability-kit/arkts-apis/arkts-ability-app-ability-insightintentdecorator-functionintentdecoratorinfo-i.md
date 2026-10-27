# FunctionIntentDecoratorInfo

```TypeScript
declare interface FunctionIntentDecoratorInfo extends IntentDecoratorInfo
```

Parameter type of the [@InsightIntentFunctionMethod](arkts-ability-app-ability-insightintentdecorator-insightintentfunctionmethod-d.md#insightintentfunctionmethod) decorator. All properties inherit from [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md).

**Inheritance/Implementation:** FunctionIntentDecoratorInfo extends [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)

**Since:** 20

<!--Device-unnamed-declare interface FunctionIntentDecoratorInfo extends IntentDecoratorInfo--><!--Device-unnamed-declare interface FunctionIntentDecoratorInfo extends IntentDecoratorInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentLink, InsightIntentPage, InsightIntentFunctionMethod, InsightIntentFunction, InsightIntentEntry, LinkParamCategory, InsightIntentForm, InsightIntentEntity } from '@kit.AbilityKit';
```

## permissions

```TypeScript
permissions?: string[]
```

Optional list of permissions required to invoke this intent. This is for caller-side query/reference only. The system does not enforce these permissions automatically. Permission validation must be implemented on the intent provider (server side).

**Type:** string[]

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-FunctionIntentDecoratorInfo-permissions?: string[]--><!--Device-FunctionIntentDecoratorInfo-permissions?: string[]-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
