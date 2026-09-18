# @InsightIntentFunction

```TypeScript
export declare const InsightIntentFunction: (() => ClassDecorator)
```

This decorator must be used together with the [@InsightIntentFunctionMethod](arkts-ability-app-ability-insightintentdecorator-insightintentfunctionmethod-d.md#insightintentfunctionmethod) decorator. This decorator is used to decorate a class, and [@InsightIntentFunctionMethod](arkts-ability-app-ability-insightintentdecorator-insightintentfunctionmethod-d.md#insightintentfunctionmethod) is used to decorate a static function in that class. This setup defines the static function as an intent, enabling AI systems to execute it rapidly.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
