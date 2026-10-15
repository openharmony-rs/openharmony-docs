# @InsightIntentEntry

```TypeScript
export declare const InsightIntentEntry: ((intentInfo: EntryIntentDecoratorInfo) => ClassDecorator)
```

Decorates a class that inherits from [InsightIntentEntryExecutor](arkts-ability-app-ability-insightintententryexecutor-insightintententryexecutor-c.md) to implement intent operations and configure the ability on which the intent depends. This helps the AI entry point to easily invoke the associated ability and perform the intended action. For details on the parameters supported by this decorator, see [EntryIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-entryintentdecoratorinfo-i.md).

> **NOTE:** 
> 
> If this decorator is used to integrate a standard intent, all mandatory parameters defined in the standard intent
> JSON Schema must be implemented and their types must match.
> If a custom intent is created, all mandatory parameters defined in the parameters field must be implemented and
> their types must match.
> The decorated class must be exported using export default. The attributes of the class support only basic types
> or intent entities, and the return value supports only intent entities.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-unnamed-export declare const InsightIntentEntry: ((intentInfo: EntryIntentDecoratorInfo) => ClassDecorator)--><!--Device-unnamed-export declare const InsightIntentEntry: ((intentInfo: EntryIntentDecoratorInfo) => ClassDecorator)-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
