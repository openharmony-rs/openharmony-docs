# @InsightIntentEntity

```TypeScript
export declare const InsightIntentEntity: ((intentEntityInfo: IntentEntityDecoratorInfo) => ClassDecorator)
```

Decorates a class that inherits from [IntentEntity](arkts-ability-insightintent-intententity-i.md) to define the class as an intent entity, which can pass parameters required for intent calls. For details on the parameters supported by this decorator, see [IntentEntityDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intententitydecoratorinfo-i.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
