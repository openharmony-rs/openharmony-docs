# @ohos.app.ability.insightIntentDriver(Intent Call Execution)

The module provides APIs for executing intent calls. The system executes intent calls based on user interaction and more.

> **NOTE:** 
> 
> Starting from API version 20, this module supports application navigation using intents defined by the
> [@InsightIntentLink](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)
> decorator.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [execute](arkts-ability-insightintentdriver-execute-f-sys.md#execute) | Executes a call to an intent. This API uses an asynchronous callback to return the result. When the caller is in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is required. When [ExecuteMode](arkts-ability-insightintent-executemode-e.md) of the intent call is set to **UI_ABILITY_BACKGROUND**, the ohos.permission.ABILITY_BACKGROUND_COMMUNICATION permission is required. On API 26.0.0 and above, intent can be executed across devices. When the intent call is cross-device, the ohos.permission.EXECUTE_DISTRIBUTED_INTENT permission is required. |
| [execute](arkts-ability-insightintentdriver-execute-f-sys.md#execute-1) | Executes a call to an intent. This API uses a promise to return the result. When the caller is in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is required. When [ExecuteMode](arkts-ability-insightintent-executemode-e.md) of the intent call is set to **UI_ABILITY_BACKGROUND**, the ohos.permission.ABILITY_BACKGROUND_COMMUNICATION permission is required. When the intent call is cross-device, the ohos.permission.EXECUTE_DISTRIBUTED_INTENT permission is required. On API 26.0.0 and above, intent can be executed across devices. When the intent call is cross-device, the ohos.permission.EXECUTE_DISTRIBUTED_INTENT permission is required. |
| [getAllInsightIntentInfo](arkts-ability-insightintentdriver-getallinsightintentinfo-f-sys.md) | Obtains the information about all intents on the current device. This API uses a promise to return the result. |
| [getInsightIntentInfoByBundleName](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md) | Obtains the intent information on the current device based on the given bundle name. This API uses a promise to return the result. |
| [getInsightIntentInfoByFilter](arkts-ability-insightintentdriver-getinsightintentinfobyfilter-f-sys.md) | Obtains the intent information on the current device based on the given intent filter. This API uses a promise to return the result.<br>If the user ID of the calling application is different from the user ID of the intent, the calling application must request the ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission. |
| [getInsightIntentInfoByIntentName](arkts-ability-insightintentdriver-getinsightintentinfobyintentname-f-sys.md) | Obtains the intent information on the current device based on the bundle name, module name, and intent name. This API uses a promise to return the result. |
| [queryEntityInfo](arkts-ability-insightintentdriver-queryentityinfo-f-sys.md) | Query insight intent entity information. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [EntityInfo](arkts-ability-insightintentdriver-entityinfo-i-sys.md) | EntityInfo inherits from [IntentEntityDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intententitydecoratorinfo-i.md) and is used to describe the information about the intent entity defined by the [@InsightIntentEntity](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity) decorator. |
| [EntryIntentInfo](arkts-ability-insightintentdriver-entryintentinfo-i-sys.md) | Describes the parameters supported by the [@InsightIntentForm](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform) decorator, such as the widget name. It also describes the widget information bound to the [intent developed using a configuration file](../../../application-models/insight-intent-config-development.md). |
| [ExecuteParam](arkts-ability-insightintentdriver-executeparam-i-sys.md) | Defines the parameter used to execute an intent call. |
| [FormIntentInfo](arkts-ability-insightintentdriver-formintentinfo-i-sys.md) | Describes the parameters supported by the [@InsightIntentForm](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform) decorator, such as the widget name. It also describes the widget information bound to the [intent developed using a configuration file](../../../application-models/insight-intent-config-development.md). |
| [FunctionIntentInfo](arkts-ability-insightintentdriver-functionintentinfo-i-sys.md) | Defines the parameter type of the [@InsightIntentFunctionMethod](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentfunctionmethod) decorator. All parameters inherit from [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md). |
| [InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md) | Defines the intent information, which is the specific parameter configuration of the intent in the device. |
| [InsightIntentInfoFilter](arkts-ability-insightintentdriver-insightintentinfofilter-i-sys.md) | Defines an intent filter, which specifies the criteria for selecting target intents. It is used to filter intents on the device that meet these criteria. |
| [LinkIntentInfo](arkts-ability-insightintentdriver-linkintentinfo-i-sys.md) | Describes the parameters supported by the [@InsightIntentLink](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator, such as the URI required for application redirection. |
| [PageIntentInfo](arkts-ability-insightintentdriver-pageintentinfo-i-sys.md) | Describes the parameters supported by the [@InsightIntentPage](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentpage) decorator, such as the [NavDestination](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10) name of the target page. |
| [QueryParam](arkts-ability-insightintentdriver-queryparam-i-sys.md) | Param when query insight intent entity. |
| [ServiceExtensionIntentInfo](arkts-ability-insightintentdriver-serviceextensionintentinfo-i-sys.md) | Describes the information of the ServiceExtensionAbility bound to the [intent developed using a configuration file](../../../application-models/insight-intent-config-development.md). |
| [SubIntentInfoForConfiguration](arkts-ability-insightintentdriver-subintentinfoforconfiguration-i-sys.md) | Describes the unique information of the [intent developed using a configuration file](../../../application-models/insight-intent-config-development.md). |
| [UIAbilityIntentInfo](arkts-ability-insightintentdriver-uiabilityintentinfo-i-sys.md) | Describes the information of the UIAbility bound to the [intent developed using a configuration file](../../../application-models/insight-intent-config-development.md). |
| [UIExtensionIntentInfo](arkts-ability-insightintentdriver-uiextensionintentinfo-i-sys.md) | Describes the information of the UIExtensionAbility bound to the [intent developed using a configuration file](../../../application-models/insight-intent-config-development.md). |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DevelopType](arkts-ability-insightintentdriver-developtype-e-sys.md) | Enumerates the modes that define how an intent is developed. |
| [ExecuteModeForConfiguration](arkts-ability-insightintentdriver-executemodeforconfiguration-e-sys.md) | Enumerates the execution modes supported by an [intent developed using a configuration file](../../../application-models/insight-intent-config-development.md). For example, if **executeMode** in the [insight_intent.json configuration file] (../../../application-models/insight-intent-config-development.md#description-of-the-insight_intentjson-file) is set to **foreground**, the intent bound to the UIAbility can run in the foreground. |
| [GetInsightIntentFlag](arkts-ability-insightintentdriver-getinsightintentflag-e-sys.md) | Enumerates the flags of intent information ([InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md)). It is used in [getAllInsightIntentInfo](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md), [getInsightIntentInfoByBundleName](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md), and [getInsightIntentInfoByIntentName](arkts-ability-insightintentdriver-getinsightintentinfobyintentname-f-sys.md). |
| [InsightIntentType](arkts-ability-insightintentdriver-insightintenttype-e-sys.md) | Enumerates the intent types defined by the intent decorator. You can obtain the intent type from [LinkIntentInfo](arkts-ability-insightintentdriver-linkintentinfo-i-sys.md) returned by calling APIs such as [getAllInsightIntentInfo](arkts-ability-insightintentdriver-getallinsightintentinfo-f-sys.md). |
<!--DelEnd-->
