# @InsightIntentForm

```TypeScript
export declare const InsightIntentForm: ((intentInfo: FormIntentDecoratorInfo) => ClassDecorator)
```

Decorates a [FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md) to specify the name of the widget bound to the [FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md). This enables the AI entry point to add the widget via intent calls. For details on the parameters supported by this decorator, see [FormIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-formintentdecoratorinfo-i.md).

> **NOTE:** 
> For details about the requirements for defining widget names, see Widget Configuration.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
