# @InsightIntentEntry

```TypeScript
export declare const InsightIntentEntry: ((intentInfo: EntryIntentDecoratorInfo) => ClassDecorator)
```

Decorates a class that inherits from [InsightIntentEntryExecutor](arkts-ability-app-ability-insightintententryexecutor-insightintententryexecutor-c.md) to implement intent operations and configure the ability on which the intent depends. This helps the AI entry point to easily invoke the associated ability and perform the intended action. For details on the parameters supported by this decorator, see [EntryIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-entryintentdecoratorinfo-i.md).

> **NOTE:** 
> 
> If this decorator is used to access a standard intent, all mandatory parameters defined in the standard intent
> JSON schema must be implemented and their parameter types must match.
> If this decorator is used to access a custom intent, all mandatory parameters defined in parameters must be
> implemented and their parameter types must match.
> Classes decorated by this decorator must be exported using export default. Class properties are limited to basic
> types or intent entities, and the return value must be intent entities.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
