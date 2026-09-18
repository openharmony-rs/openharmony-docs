# @InsightIntentFunctionMethod

```TypeScript
export declare const InsightIntentFunctionMethod: ((intentInfo: FunctionIntentDecoratorInfo) => MethodDecorator)
```

This decorator must be used together with the [@InsightIntentFunction](arkts-ability-app-ability-insightintentdecorator-insightintentfunction-d.md#insightintentfunction) decorator. [@InsightIntentFunction](arkts-ability-app-ability-insightintentdecorator-insightintentfunction-d.md#insightintentfunction) is used to decorate a class, and this decorator is used to decorate a static function in that class. This setup defines the static function as an intent, enabling AI systems to execute it rapidly.

> **NOTE:** 
> 
> The class containing static methods must be exported using export.
> Parameter names and types of a function must align with those specified in the intent definition.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
