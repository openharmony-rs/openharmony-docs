# @InsightIntentLink

```TypeScript
export declare const InsightIntentLink: ((intentInfo: LinkIntentDecoratorInfo) => ClassDecorator)
```

Decorates a URI link in the current application as an intent, enabling AI entries to quickly jump to the current application via the defined intent. For details on the parameters supported by this decorator, see [LinkIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-linkintentdecoratorinfo-i.md).

> **NOTE:** 
> The URI format must comply with the requirements described in
> [Application Link Description](../../../application-models/app-uri-config.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-unnamed-export declare const InsightIntentLink: ((intentInfo: LinkIntentDecoratorInfo) => ClassDecorator)--><!--Device-unnamed-export declare const InsightIntentLink: ((intentInfo: LinkIntentDecoratorInfo) => ClassDecorator)-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
