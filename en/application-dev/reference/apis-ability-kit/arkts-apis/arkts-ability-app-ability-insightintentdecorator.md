# @ohos.app.ability.InsightIntentDecorator(Intent Decorator)

The InsightIntentDecorator module provides several types of intent decorators for decorating classes or methods. You
 can [use these decorators to develop intents](../../../application-models/insight-intent-decorator-development.md),
 define application functionalities as intents, and integrate them into AI entry points such as intelligent Q&A,
 intelligent search, and intelligent recommendation systems.

-
 [@InsightIntentLink](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)
 : decorates a URI in your application as an intent, enabling AI systems to quickly jump to your application via this
 intent. For details on the parameters supported by this decorator, see
 [LinkIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-linkintentdecoratorinfo-i.md).
 -
 [@InsightIntentPage](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentpage)
 : decorates a page in your application as an intent, enabling AI systems to swiftly navigate to that page. For
 details on the parameters supported by this decorator, see [PageIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-pageintentdecoratorinfo-i.md).
 -
 [@InsightIntentFunction](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentfunction)
 and
 [@InsightIntentFunctionMethod](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentfunctionmethod)
 : The two decorators must be used together.
 [@InsightIntentFunction](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentfunction)
 is used to decorate a class, and
 [@InsightIntentFunctionMethod](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentfunctionmethod)
 is used to decorate a static function in that class. This setup defines the static function as an intent, enabling
 AI systems to execute it rapidly.
 -
 [@InsightIntentEntry](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententry)
 : decorates a class that inherits from
 [InsightIntentEntryExecutor](arkts-ability-app-ability-insightintententryexecutor-insightintententryexecutor-c.md) to
 implement intent operations and configure the ability on which the intent depends. This helps the AI entry point to
 easily invoke the associated ability and perform the intended action. For details on the parameters supported by this
 decorator, see [EntryIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-entryintentdecoratorinfo-i.md).
 -
 [@InsightIntentForm](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform)
 : decorates a [FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md) to specify the name of the widget
 bound to the FormExtensionAbility. This enables the AI entry point to add the widget via intent calls. For details on
 the parameters supported by this decorator, see [FormIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-formintentdecoratorinfo-i.md).
 -
 [@InsightIntentEntity](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)
 : decorates a class that inherits from
 [IntentEntity](arkts-ability-insightintent-intententity-i.md) to define the class as an intent
 entity, which can pass parameters required for intent calls. For details on the parameters supported by this
 decorator, see [IntentEntityDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intententitydecoratorinfo-i.md).



## Modules to Import

```TypeScript
import { InsightIntentLink, InsightIntentPage, InsightIntentFunctionMethod, InsightIntentFunction, InsightIntentEntry, LinkParamCategory, InsightIntentForm, InsightIntentEntity } from '@kit.AbilityKit';
```

## Summary

### Decorators

| Name | Description |
| --- | --- |
| [@InsightIntentEntity](arkts-ability-app-ability-insightintentdecorator-insightintententity-d.md#insightintententity) | Decorates a class that inherits from [IntentEntity](arkts-ability-insightintent-intententity-i.md) to define the class as an intent entity, which can pass parameters required for intent calls. For details on the parameters supported by this decorator, see [IntentEntityDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intententitydecoratorinfo-i.md). |
| [@InsightIntentEntry](arkts-ability-app-ability-insightintentdecorator-insightintententry-d.md#insightintententry) | Decorates a class that inherits from [InsightIntentEntryExecutor](arkts-ability-app-ability-insightintententryexecutor-insightintententryexecutor-c.md) to implement intent operations and configure the ability on which the intent depends. This helps the AI entry point to easily invoke the associated ability and perform the intended action. For details on the parameters supported by this decorator, see [EntryIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-entryintentdecoratorinfo-i.md). |
| [@InsightIntentForm](arkts-ability-app-ability-insightintentdecorator-insightintentform-d.md#insightintentform) | Decorates a [FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md) to specify the name of the widget bound to the [FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md). This enables the AI entry point to add the widget via intent calls. For details on the parameters supported by this decorator, see [FormIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-formintentdecoratorinfo-i.md). |
| [@InsightIntentFunction](arkts-ability-app-ability-insightintentdecorator-insightintentfunction-d.md#insightintentfunction) | This decorator must be used together with the [@InsightIntentFunctionMethod](arkts-ability-app-ability-insightintentdecorator-insightintentfunctionmethod-d.md#insightintentfunctionmethod) decorator. This decorator is used to decorate a class, and [@InsightIntentFunctionMethod](arkts-ability-app-ability-insightintentdecorator-insightintentfunctionmethod-d.md#insightintentfunctionmethod) is used to decorate a static function in that class. This setup defines the static function as an intent, enabling AI systems to execute it rapidly. |
| [@InsightIntentFunctionMethod](arkts-ability-app-ability-insightintentdecorator-insightintentfunctionmethod-d.md#insightintentfunctionmethod) | This decorator must be used together with the [@InsightIntentFunction](arkts-ability-app-ability-insightintentdecorator-insightintentfunction-d.md#insightintentfunction) decorator. [@InsightIntentFunction](arkts-ability-app-ability-insightintentdecorator-insightintentfunction-d.md#insightintentfunction) is used to decorate a class, and this decorator is used to decorate a static function in that class. This setup defines the static function as an intent, enabling AI systems to execute it rapidly. |
| [@InsightIntentLink](arkts-ability-app-ability-insightintentdecorator-insightintentlink-d.md#insightintentlink) | Define InsightIntentLink. |
| [@InsightIntentPage](arkts-ability-app-ability-insightintentdecorator-insightintentpage-d.md#insightintentpage) | Decorates a page in the application as an intent, enabling AI systems to swiftly navigate to that page. For details on the parameters supported by this decorator, see [PageIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-pageintentdecoratorinfo-i.md). |

### Interfaces

| Name | Description |
| --- | --- |
| [EntryIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-entryintentdecoratorinfo-i.md) | Inherits from [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md) and is used to describe the parameters supported by the [@InsightIntentEntry](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententry) decorator. |
| [FormIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-formintentdecoratorinfo-i.md) | Inherits from [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md) and is used to describe the parameters supported by the [@InsightIntentForm](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform) decorator. |
| [FunctionIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-functionintentdecoratorinfo-i.md) | Parameter type of the [@InsightIntentFunctionMethod](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentfunctionmethod) decorator. All properties inherit from [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md). |
| [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md) | Common properties for intent decorators, used to define basic information about an intent (including the intent name and version number). It applies to all decorators provided by this module. |
| [IntentEntityDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intententitydecoratorinfo-i.md) | Describes the parameters supported by the [@InsightIntentEntity](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity) decorator. |
| [LinkIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-linkintentdecoratorinfo-i.md) | LinkIntentDecoratorInfo inherits from [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md) and describes the parameters supported by the [@InsightIntentLink](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator, such as the URI information required for application redirection. |
| [LinkIntentParamMapping](arkts-ability-app-ability-insightintentdecorator-linkintentparammapping-i.md) | LinkIntentParamMapping defines the mapping between intent parameters and URI information for the [@InsightIntentLink](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator. |
| [PageIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-pageintentdecoratorinfo-i.md) | PageIntentDecoratorInfo inherits from [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md) and describes the parameters supported by the [@InsightIntentPage](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentpage) decorator, such as the name of [NavDestination](../../apis-arkui/arkts-components/arkts-arkui-navigation-comp-attribute.md#navdestination) of the target page. |

### Enums

| Name | Description |
| --- | --- |
| [LinkParamCategory](arkts-ability-app-ability-insightintentdecorator-linkparamcategory-e.md) | Enumerates the intent parameter categories available for the [@InsightIntentLink](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator. The enum is used to define how intent parameters should be passed. |
