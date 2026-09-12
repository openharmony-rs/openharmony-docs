# @ohos.app.ability.insightIntentDriver (Intent Call Execution) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T12:40:03.649Z pushedAt=2026-09-05T10:47:30.959Z -->

The module provides APIs for executing intent calls. The system executes intent calls based on user interaction and more.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs provided by this module are system APIs.
>
> Starting from API version 20, this module supports application navigation using intents defined by the [@InsightIntentLink](js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator.

## Modules to Import

```ts
import { insightIntentDriver } from '@kit.AbilityKit';
```

## ExecuteParam

Defines the parameter used to execute an intent call.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | --- |----- | -------- |
| bundleName | string | No | No | Bundle name of the application to which the Ability for intent invocation belongs. |
| moduleName | string | No | No | Module name to which the Ability for intent invocation belongs. |
| abilityName | string | No | No | Name of the Ability for intent invocation. If the intent defined by the [@InsightIntentLink](js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator is used to implement application redirection, pass an empty string for this field. |
| insightIntentName | string | No | No | Name of the intent invocation. |
| insightIntentParam | Record\<string, Object> | No | No | Parameters of the intent invocation. |
| executeMode | [insightIntent.ExecuteMode](js-apis-app-ability-insightIntent.md#executemode) | No | No | Execution mode of the intent invocation. If the intent defined by the [@InsightIntentLink](js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator is used to implement application redirection, this field must be filled in (any value in the ExecuteMode enum can be used), but it does not affect the actual execution logic of application redirection. |
| displayId<sup>12+</sup> | number | No | Yes | Physical screen ID specified during intent invocation. This parameter must be an integer and takes effect only when executeMode is UI_ABILITY_FOREGROUND. |
| uris<sup>18+</sup> | Array&lt;string&gt; | No | Yes | List of URIs authorized by the intent invoker to the intent executor during intent invocation. If the intent defined by the [@InsightIntentLink](js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator is used to implement application redirection, this field is mandatory, and only the first element of the array is read as the URI of [openLink](js-apis-inner-application-uiAbilityContext.md#openlink12). |
| flags<sup>18+</sup> | number | No | Yes | [Flags](js-apis-app-ability-wantConstant.md#flags) of the URIs authorized by the intent invoker to the intent executor during intent invocation. <br>**Note:**<br>This parameter supports only FLAG_AUTH_READ_URI_PERMISSION, FLAG_AUTH_WRITE_URI_PERMISSION, and FLAG_AUTH_READ_URI_PERMISSION\|FLAG_AUTH_WRITE_URI_PERMISSION.|
| userId<sup>23+</sup> | number | No | Yes | User ID to which the target intent belongs.<br>**Note:**<br>If the user ID of the calling application differs from the user ID to which the target intent belongs, the permission `ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS` must be requested.    |
| deviceId | string | No | Yes | ID of the target device to connect to.<br>**Note:**<br>If the device ID of the calling application differs from the device ID to which the target intent belongs, the permission `ohos.permission.EXECUTE_DISTRIBUTED_INTENT` must be requested.<br>**Since:** 26.0.0    |

## InsightIntentInfoFilter<sup>23+</sup>

Defines an intent filter, which specifies the criteria for selecting target intents. It is used to filter intents on the device that meet these criteria.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name       | Type  | Read-Only| Optional| Description                                                        |
| ----------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| intentFlags | number | No  | No  | Flag of the intent information ([InsightIntentInfo](#insightintentinfo20)). It is used to query full or brief intent information. For details, see [GetInsightIntentFlag](#getinsightintentflag20).|
| bundleName  | string | No  | Yes  | Bundle name of the application to which the intent belongs.                                                |
| moduleName  | string | No  | Yes  | Module name of the application to which the intent belongs.                                                  |
| intentName  | string | No  | Yes  | Intent name.                                                  |
| userId      | number | No  | Yes  | ID of the user to which the intent belongs.<br>**NOTE**<br>If the user ID of the calling application is different from the user ID of the intent, the calling application must request the ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission.  |
## InsightIntentType<sup>20+</sup>

Enumerates the intent types defined by the intent decorator. You can obtain the intent type from [LinkIntentInfo](#linkintentinfo20) returned by calling APIs such as [getAllInsightIntentInfo](#insightintentdrivergetallinsightintentinfo20).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Value| Description|
| -------- | -------- | -------- |
| LINK | @InsightIntentLink | A decorator of the [@InsightIntentLink](./js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) type.|
| PAGE | @InsightIntentPage | A decorator of the [@InsightIntentPage](./js-apis-app-ability-InsightIntentDecorator.md#insightintentpage) type.|
| ENTRY | @InsightIntentEntry | A decorator of the [@InsightIntentEntry](./js-apis-app-ability-InsightIntentDecorator.md#insightintententry) type.|
| FUNCTION | @InsightIntentFunctionMethod | A decorator of the [@InsightIntentFunctionMethod](./js-apis-app-ability-InsightIntentDecorator.md#insightintentfunctionmethod) type.|
| FORM | @InsightIntentForm | A decorator of the [@InsightIntentForm](./js-apis-app-ability-InsightIntentDecorator.md#insightintentform) type.|

## ExecuteModeForConfiguration<sup>23+</sup>

Enumerates the execution modes supported by an [intent developed using a configuration file](../../application-models/insight-intent-config-development.md). For example, if **executeMode** in the [insight_intent.json configuration file](../../application-models/insight-intent-config-development.md#description-of-the-insight_intentjson-file) is set to **foreground**, the intent bound to the UIAbility can run in the foreground.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Value| Description|
| -------- | -------- | -------- |
| FOREGROUND | 0 | The intent bound to the UIAbility can run in the foreground.|
| BACKGROUND | 1 | The intent bound to the UIAbility can run in the background.|

## LinkIntentInfo<sup>20+</sup>

Describes the parameters supported by the [@InsightIntentLink](./js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator, such as the URI required for application redirection.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- |-------- |
| uri | string | Yes| No| URI of an intent.|

## PageIntentInfo<sup>20+</sup>

PageIntentInfo is used to describe the parameters supported by the [@InsightIntentPage](./js-apis-app-ability-InsightIntentDecorator.md#insightintentpage) decorator, for example, the [navDestination](../apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10) name of the target page.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- |-------- |
| uiAbility | string | Yes | No | Name of the UIAbility component. |
| pagePath | string | Yes| No| Page name.|
| navigationId | string | Yes| No|  ID of the [Navigation](../apis-arkui/arkui-ts/ts-basic-components-navigation.md) component bound to the intent.|
| navDestinationName | string | Yes | No | Name of the [navDestination](../apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10) component bound to the intent. |

## FunctionIntentInfo<sup>20+</sup>

Defines the parameter type of the [@InsightIntentFunctionMethod](./js-apis-app-ability-InsightIntentDecorator.md#insightintentfunctionmethod) decorator. All parameters inherit from [IntentDecoratorInfo](./js-apis-app-ability-InsightIntentDecorator.md#intentdecoratorinfo).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

## FormIntentInfo<sup>20+</sup>

Describes the parameters supported by the [@InsightIntentForm](./js-apis-app-ability-InsightIntentDecorator.md#insightintentform) decorator, such as the widget name. It also describes the widget information bound to the [intent developed using a configuration file](../../application-models/insight-intent-config-development.md).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- |-------- |
| abilityName | string | Yes| No| Ability name.|
| formName | string | Yes| No| Name of the widget bound to the [FormExtensionAbility](../apis-form-kit/js-apis-app-form-formExtensionAbility.md).|

## EntryIntentInfo<sup>20+</sup>

Describes the parameters supported by the [@InsightIntentEntry](./js-apis-app-ability-InsightIntentDecorator.md#insightintententry) decorator, such as the intent execution mode.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- |-------- |
| abilityName | string | Yes| No| Ability name.|
| executeMode | [insightIntent.ExecuteMode](./js-apis-app-ability-insightIntent.md#executemode)[] | Yes| No| Intent execution mode. that is, execution mode supported when the bound ability is started.|

## SubIntentInfoForConfiguration<sup>23+</sup>

Describes the unique information of the [intent developed using a configuration file](../../application-models/insight-intent-config-development.md).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- |-------- |
| srcEntry | string | Yes| No| Relative path of the intent execution file. The value is a string of a maximum of 127 bytes.|
| inputParams | Array&lt;Record\<string, Object\>&gt; | Yes| Yes| Data format of intent parameters, which is used to define the input data format during intent calls.|
| outputParams | Array&lt;Record\<string, Object\>&gt; | Yes| Yes| Data format for the results returned by intent calls. It defines how the data should be structured.|
| uiAbility | [UIAbilityIntentInfo](#uiabilityintentinfo23) | Yes| Yes| Information about the UIAbility bound to the intent, including the **ability** and **executeMode** fields.|
| uiExtension | [UIExtensionIntentInfo](#uiextensionintentinfo23) | Yes| Yes| Information about the UIExtensionAbility bound to the intent.|
| form | [FormIntentInfo](#formintentinfo20) | Yes | Yes | Indicates the card information bound to the intent. |
| serviceExtension | [ServiceExtensionIntentInfo](#serviceextensionintentinfo23) | Yes| Yes| Information about the ServiceExtensionAbility bound to the intent.|
| entities | Record\<string, Object\> | Yes| Yes| Entity information contained in the intent.|

## UIAbilityIntentInfo<sup>23+</sup>

Describes the information of the UIAbility bound to the [intent developed using a configuration file](../../application-models/insight-intent-config-development.md).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- |-------- |
| abilityName | string | Yes| No| Name of the UIAbility bound to the intent.|
| executeMode | [ExecuteModeForConfiguration](#executemodeforconfiguration23)[] | Yes| No| Intent execution mode.|

## UIExtensionIntentInfo<sup>23+</sup>

Describes the information of the UIExtensionAbility bound to the [intent developed using a configuration file](../../application-models/insight-intent-config-development.md).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- |-------- |
| abilityName | string | Yes| No| Name of the UIExtensionAbility bound to the intent.|

## ServiceExtensionIntentInfo<sup>23+</sup>

Describes the information of the ServiceExtensionAbility bound to the [intent developed using a configuration file](../../application-models/insight-intent-config-development.md).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- |-------- |
| abilityName | string | Yes| No| Name of the ServiceExtensionAbility bound to the intent.|

## DevelopType<sup>23+</sup>

Enumerates the modes that define how an intent is developed.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Value| Description|
| -------- | -------- | -------- |
| CONFIGURATION  | 'configuration' | The intent is developed using a configuration file.|
| DECORATOR | 'decorator' | The intent is developed using a decorator.|

## EntityInfo<sup>20+</sup>

EntityInfo inherits from [IntentEntityDecoratorInfo](./js-apis-app-ability-InsightIntentDecorator.md#intententitydecoratorinfo) and is used to describe the information about the intent entity defined by the [@InsightIntentEntity](./js-apis-app-ability-InsightIntentDecorator.md#insightintententity) decorator.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- |-------- |
| className | string | Yes| No| Class name decorated by [@InsightIntentEntity](./js-apis-app-ability-InsightIntentDecorator.md#insightintententity).|
| entityId | string | Yes| No| ID of the intent entity.|
| entityCategory | string | Yes| No| Category of the intent entity.|
| parameters | Record\<string, Object> | Yes | No | Data format declaration of the intent entity parameters, used to define the data format of entity parameters during intent invocation. |
| parentClassName | string | Yes| No| Parent class name decorated by [@InsightIntentEntity](./js-apis-app-ability-InsightIntentDecorator.md#insightintententity).|
| isQueryable | boolean | Yes | Yes | Whether the intent entity class decorated by [@InsightIntentEntity](./js-apis-app-ability-InsightIntentDecorator.md#insightintententity) supports query. Only intent entities inherited from the [insightIntent.AppIntentEntity](./js-apis-app-ability-insightIntent.md#appintententity) class support query.<br/> - true: query is supported.<br/> - false: query is not supported.<br/>**Since:** 26.0.0 |
| supportedQueryProperties | string[] | Yes | Yes | Properties through which the intent entity decorated by [@InsightIntentEntity](./js-apis-app-ability-InsightIntentDecorator.md#insightintententity) supports query. The key value of the intent entity query parameter [parameters](./js-apis-app-ability-insightIntent.md#queryentityparam) must be in this property list.<br/>**Since:** 26.0.0 |

## InsightIntentInfo<sup>20+</sup>

Defines the intent information, which is the specific parameter configuration of the intent in the device.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- |-------- |
| bundleName | string | Yes| No| Bundle name of the application.|
| moduleName | string | Yes| No| Module name.|
| intentName | string | Yes| No| Intent name.|
| domain | string | Yes| No| Vertical domain of the intent. It is used to categorize intents by vertical fields (for example, video, music, and games). For details about the value range, see the vertical domain fields in smart distribution features in different vertical domains.|
| intentVersion | string | Yes| No| Version number of the intent. It is used to distinguish and manage intents when their capabilities evolve.|
| displayName | string | Yes| No| Name of the intent displayed in the InsightIntent framework.|
| displayDescription | string | Yes| No| Description of the intent displayed in the InsightIntent framework.|
| schema | string | Yes| No| Standard intent name. If an intent in the standard intent list matches both the **schema** and **intentVersion** fields, it is processed as a standard intent.|
| icon | string | Yes| No| Icon of the intent.|
| llmDescription | string | Yes| No| Function of an intent, which helps large language models understand the intent.|
| keywords | string[] | Yes| No| Search keywords for the intent.|
| intentType | [InsightIntentType](#insightintenttype20) | Yes | No | Represents the intent type defined by the intent decorator.<br/>**Note:**<br/>For intents developed using the configuration file, the default return value of this field is the [@InsightIntentEntry](./js-apis-app-ability-InsightIntentDecorator.md#insightintententry) type decorator. |
| subIntentInfo | [LinkIntentInfo](#linkintentinfo20) \| [PageIntentInfo](#pageintentinfo20) \| [FunctionIntentInfo](#functionintentinfo20) \| [FormIntentInfo](#formintentinfo20) \| [EntryIntentInfo](#entryintentinfo20) | Yes | No | Represents the intent information of a specific intent decorator. <br/>**Note:**<br/>For intents developed using the configuration file, the default return value of this field is [EntryIntentInfo](#entryintentinfo20). |
| parameters | Record<string, Object> | Yes| No| Data format of intent parameters, which is used to define the input data format during intent calls.|
| result | Record<string, Object> | Yes| No| Execution result returned.|
| entities | Array&lt;[EntityInfo](#entityinfo20)&gt; | Yes| No| Entity information contained in the intent.|
| subIntentInfoForConfiguration<sup>23+</sup> | [SubIntentInfoForConfiguration](#subintentinfoforconfiguration23) | Yes| Yes| Unique information about the intent developed using a configuration file.|
| developType<sup>23+</sup> | [DevelopType](#developtype23) | Yes| Yes| Development mode of the intent.|

## GetInsightIntentFlag<sup>20+</sup>

Enumerates the flags of intent information ([InsightIntentInfo](#insightintentinfo20)). It is used in [getAllInsightIntentInfo](#insightintentdrivergetinsightintentinfobybundlename20), [getInsightIntentInfoByBundleName](#insightintentdrivergetinsightintentinfobybundlename20), and [getInsightIntentInfoByIntentName](#insightintentdrivergetinsightintentinfobyintentname20).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Value| Description|
| -------- | -------- | -------- |
| GET_FULL_INSIGHT_INTENT | 0x00000001 | Used to query all intent information (except entities) in [InsightIntentInfo](#insightintentinfo20). To query entities information, use **GET_ENTITY_INFO**.|
| GET_SUMMARY_INSIGHT_INTENT | 0x00000002 | Used to query brief intent information in [InsightIntentInfo](#insightintentinfo20).|
| GET_ENTITY_INFO | 0x00000004 | Queries the information of [EntityInfo](#entityinfo20). It cannot be used alone and must be used together with GET_FULL_INSIGHT_INTENT or GET_SUMMARY_INSIGHT_INTENT. For example, `GET_FULL_INSIGHT_INTENT \| GET_ENTITY_INFO`. |

> **NOTE**
>
>  - For intents developed using a configuration file, the full and brief information queried through the preceding APIs are the same.
>  - For intents developed using a decorator, the full and brief information queried through the preceding APIs are different, as described below.

Table 1 Differences between full intent information and brief intent information

| Name| Included in Full Intent Information| Included in Brief Intent Information|
| -------- | -------- | -------- |
| bundleName | Yes| Yes| 
| moduleName | Yes| Yes|
| intentName | Yes| Yes|
| domain | Yes| No|
| intentVersion | Yes| No|
| displayName | Yes| Yes|
| displayDescription | Yes| No|
| schema | Yes| No|
| icon | Yes| No|
| llmDescription | Yes| No|
| keywords | Yes| No|
| intentType | Yes| Yes|
| subIntentInfo | Yes| Yes|
| parameters | Yes| Yes|
| entities | No| No|
| developType<sup>23+</sup> | Yes| Yes|
| subIntentInfoForConfiguration<sup>23+</sup> | No| No|

## QueryParam

Intent entity query parameters, used to filter intent entities on the device that meet matching conditions.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| bundleName  | string | No   | No   | Bundle name of the application to which the target intent entity belongs. |
| moduleName  | string | No   | No   | Module name to which the target intent entity belongs. |
| intentName  | string | No   | No   | Intent name to which the target intent entity belongs. |
| className | string | No | No | Class name of the target intent entity decorated by [@InsightIntentEntity](./js-apis-app-ability-InsightIntentDecorator.md#insightintententity). |
| queryEntityParam | [insightIntent.QueryEntityParam](./js-apis-app-ability-insightIntent.md#queryentityparam) | No | No | Intent entity query parameters, including the query mode and query conditions, used to specify how intent entities are queried. |
| userId      | number | No   | Yes   | User ID to which the target intent entity belongs.<br/>**NOTE**<br/>If the user ID of the caller application differs from the user ID to which the target intent entity belongs, the `ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS` permission is required.   |

## insightIntentDriver.execute

execute(param: ExecuteParam, callback: AsyncCallback<insightIntent.ExecuteResult>): void

Executes a call to an intent. This API uses an asynchronous callback to return the result.

When the caller is in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is required.

When [ExecuteMode](js-apis-app-ability-insightIntent.md#executemode) of the intent call is set to **UI_ABILITY_BACKGROUND**, the ohos.permission.ABILITY_BACKGROUND_COMMUNICATION permission is required.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions**: ohos.permission.EXECUTE_INSIGHT_INTENT

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | param | [ExecuteParam](#executeparam) | Yes| Parameter used to execute the intent call.|
  | callback | AsyncCallback<[insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult)> | Yes| Callback used to return the intent call execution result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error code ID | Error message |
| -------- | -------- |
| 201      | Permission denied. |
| 202      | Not system application. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000137 | Cross-device execution failed due to a connection error. <br>Applicable version: 26.0.0+ |
| 16000138 | Device disconnected during cross-device intent execution. <br>Applicable version: 26.0.0+ |

**Example**

```ts
  import { insightIntentDriver, insightIntent } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  function executeInsightIntentAsync() {
    let param: insightIntentDriver.ExecuteParam = {
      bundleName: 'com.ohos.intentexecutedemo',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      insightIntentName: 'PlayMusic',
      insightIntentParam: {
        songName: 'City Of Stars',
      },
      executeMode: insightIntent.ExecuteMode.UI_ABILITY_FOREGROUND,
    };

    try {
      insightIntentDriver.execute(param, (error, data: insightIntent.ExecuteResult) => {
        if (error) {
          hilog.error(0x0000, 'testTag', 'execute insight intent failed with %{public}s', JSON.stringify(error));
        } else {
          hilog.info(0x0000, 'testTag', '%{public}s', 'execute insight intent succeed');
        }
        hilog.info(0x0000, 'testTag', 'execute insight intent return %{public}d', data.code);
        hilog.info(0x0000, 'testTag', 'execute insight intent result %{public}s', JSON.stringify(data.result));
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'execute insight intent error caught %{public}s', JSON.stringify(error));
    }
  }
```

## insightIntentDriver.execute

execute(param: ExecuteParam): Promise<insightIntent.ExecuteResult>

Executes a call to an intent. This API uses a promise to return the result.

When the caller is in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is required.

When [ExecuteMode](js-apis-app-ability-insightIntent.md#executemode) of the intent call is set to **UI_ABILITY_BACKGROUND**, the ohos.permission.ABILITY_BACKGROUND_COMMUNICATION permission is required.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions**: ohos.permission.EXECUTE_INSIGHT_INTENT

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | param | [ExecuteParam](#executeparam) | Yes| Parameter used to execute the intent call.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise<[insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult)> | Promise used to return the intent call execution result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error code ID | Error message |
| -------- | -------- |
| 201      | Permission denied. |
| 202      | Not system application. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000137 | Cross-device execution failed due to a connection error. <br>Applicable version: 26.0.0+ |
| 16000138 | Device disconnected during cross-device intent execution. <br>Applicable version: 26.0.0+ |

**Example**

```ts
  import { insightIntentDriver, insightIntent } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function executeSearchMusicIntentPromise() {
    let param: insightIntentDriver.ExecuteParam = {
      bundleName: 'com.ohos.intentexecutedemo',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      insightIntentName: 'PlayMusic',
      insightIntentParam: {
        songName: 'City Of Stars',
      },
      executeMode: insightIntent.ExecuteMode.UI_ABILITY_FOREGROUND,
    };

    try {
      let resultData: insightIntent.ExecuteResult = await insightIntentDriver.execute(param);
      hilog.info(0x0000, 'testTag', 'execute insight intent return %{public}d', resultData.code);
      hilog.info(0x0000, 'testTag', 'execute insight intent result %{public}s', JSON.stringify(resultData.result));
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'execute insight intent error caught %{public}s', JSON.stringify(error));
    }
  }
```

## insightIntentDriver.getAllInsightIntentInfo<sup>20+</sup>

getAllInsightIntentInfo(intentFlags: number): Promise<Array\<[InsightIntentInfo](#insightintentinfo20)>>

Obtains the information about all intents on the current device. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | intentFlags | number | Yes| Flag of the intent information ([InsightIntentInfo](#insightintentinfo20)). It is used to query full or brief intent information. For details, see [GetInsightIntentFlag](#getinsightintentflag20).|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise<Array\<[InsightIntentInfo](#insightintentinfo20)>> | Promise used to return an array holding InsightIntentInfo objects.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | -------- |
| 201      | Permission denied. |
| 202      | Not system application. |
| 16000050 | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |

**Example**

```ts
  import { insightIntentDriver } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function getInfos() {
    try {
      insightIntentDriver.getAllInsightIntentInfo(insightIntentDriver.GetInsightIntentFlag.GET_FULL_INSIGHT_INTENT | insightIntentDriver.GetInsightIntentFlag.GET_ENTITY_INFO).then((data) => {
        hilog.info(0x0000, 'testTag', 'getAllInsightIntentInfo return %{public}s', JSON.stringify(data));
      }).catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', 'getAllInsightIntentInfo errCode: %{public}d', err.code);
        hilog.error(0x0000, 'testTag', 'getAllInsightIntentInfo errMessage: %{public}s', err.message);
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'getAllInsightIntentInfo error caught %{public}s', JSON.stringify(error));
    }
  }
```

## insightIntentDriver.getInsightIntentInfoByBundleName<sup>20+</sup>

getInsightIntentInfoByBundleName(bundleName: string, intentFlags: number): Promise<Array\<[InsightIntentInfo](#insightintentinfo20)>>

Obtains the intent information on the current device based on the given bundle name. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | bundleName | string | Yes| Bundle name of the application.<br>**NOTE**<br> If the bundle name does not exist, an empty array is returned.|
  | intentFlags | number | Yes| Flag of the intent information ([InsightIntentInfo](#insightintentinfo20)). It is used to query full or brief intent information. For details, see [GetInsightIntentFlag](#getinsightintentflag20).|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise<Array\<[InsightIntentInfo](#insightintentinfo20)>> | Promise used to return an array holding InsightIntentInfo objects.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | -------- |
| 201      | Permission denied. |
| 202      | Not system application. |
| 16000050 | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module.  |

**Example**

```ts
  import { insightIntentDriver } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function getInfosByBundleName() {
    try {
      let bundleName = "com.example.intent"; // Use the actual bundle name.
      insightIntentDriver.getInsightIntentInfoByBundleName(bundleName, insightIntentDriver.GetInsightIntentFlag.GET_FULL_INSIGHT_INTENT | insightIntentDriver.GetInsightIntentFlag.GET_ENTITY_INFO).then((data) => {
        hilog.info(0x0000, 'testTag', 'getInsightIntentInfoByBundleName return %{public}s', JSON.stringify(data));
      }).catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByBundleName errCode: %{public}d', err.code);
        hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByBundleName errMessage: %{public}s', err.message);
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByBundleName error caught %{public}s', JSON.stringify(error));
    }
  }
```

## insightIntentDriver.getInsightIntentInfoByIntentName<sup>20+</sup>

getInsightIntentInfoByIntentName(bundleName: string, moduleName: string, intentName: string, intentFlags: number): Promise<[InsightIntentInfo](#insightintentinfo20)>

Obtains the intent information on the current device based on the bundle name, module name, and intent name. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | bundleName | string | Yes| Bundle name of the application.<br>**NOTE**<br> If the bundle name does not exist, an empty object is returned.|
  | moduleName | string | Yes| Module name<br>**NOTE**<br> If the module name does not exist, an empty object is returned.|
  | intentName | string | Yes| Intent name.<br>**NOTE**<br> If the intent name does not exist, an empty object is returned.|
  | intentFlags | number | Yes| Flag of the intent information ([InsightIntentInfo](#insightintentinfo20)). It is used to query full or brief intent information. For details, see [GetInsightIntentFlag](#getinsightintentflag20).|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise<[InsightIntentInfo](#insightintentinfo20)> | Promise used to return the InsightIntentInfo object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | -------- |
| 201      | Permission denied. |
| 202      | Not system application. |
| 16000050 | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module.  |

**Example**

```ts
  import { insightIntentDriver } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  function getInfoByIntentName() {
    try {
      let bundleName = "com.example.intent"; // Use the actual bundle name.
      let moduleName = "entry"; // Use the actual module name.
      let intentName = "PlayMusic"; // Modify it to the actual intent name.
      insightIntentDriver.getInsightIntentInfoByIntentName(
        bundleName, moduleName, intentName, insightIntentDriver.GetInsightIntentFlag.GET_FULL_INSIGHT_INTENT | insightIntentDriver.GetInsightIntentFlag.GET_ENTITY_INFO)
      .then((data) => {
        hilog.info(0x0000, 'testTag', 'getInsightIntentInfoByIntentName return %{public}s', JSON.stringify(data));
      }).catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByIntentName errCode: %{public}d', err.code);
        hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByIntentName errMessage: %{public}s', err.message);
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByIntentName error caught %{public}s', JSON.stringify(error));
    }
  }
```

## insightIntentDriver.getInsightIntentInfoByFilter<sup>23+</sup>

getInsightIntentInfoByFilter(filter: InsightIntentInfoFilter): Promise<Array\<InsightIntentInfo>>

Obtains the intent information on the current device based on the given intent filter. This API uses a promise to return the result.<br>If the user ID of the calling application is different from the user ID of the intent, the calling application must request the ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name                 | Type                                                 | Mandatory| Description                    |
| ----------------------- | ----------------------------------------------------- | ---- | ------------------------ |
| filter | [InsightIntentInfoFilter](#insightintentinfofilter23) | Yes  | Intent filter, which specifies the criteria for selecting a target intent. It is used to filter intents on the device that meet these criteria.|

**Return value**

| Type                                                      | Description                               |
| ---------------------------------------------------------- | ----------------------------------- |
| Promise<Array\<[InsightIntentInfo](#insightintentinfo20)>> | Promise used to return an array holding InsightIntentInfo objects.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Not system application.                                      |
| 16000006 | Cross-user operations are not allowed.                       |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module.|

**Example**

```ts
import { insightIntentDriver } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

function getInfoByFilter() {
  let filter: insightIntentDriver.InsightIntentInfoFilter = {
    intentFlags: insightIntentDriver.GetInsightIntentFlag.GET_FULL_INSIGHT_INTENT | insightIntentDriver.GetInsightIntentFlag.GET_ENTITY_INFO,
    bundleName: 'com.example.intent', // Use the actual bundle name.
    moduleName: 'entry', // Use the actual module name.
    intentName: 'PlayMusic', // The developer needs to change it to the actual intent name.
    userId: 100, // Use the actual user ID.
  };

  try {
    insightIntentDriver.getInsightIntentInfoByFilter(filter).then((data) => {
      hilog.info(0x0000, 'testTag', 'getInsightIntentInfoByFilter return %{public}s', JSON.stringify(data));
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByFilter errCode: %{public}d', err.code);
      hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByFilter errMessage: %{public}s', err.message);
    });
  } catch (error) {
    hilog.error(0x0000, 'testTag', 'getInsightIntentInfoByFilter error caught %{public}s', JSON.stringify(error));
  }
}
```

## insightIntentDriver.queryEntityInfo

queryEntityInfo(param: QueryParam): Promise\<Array\<Record\<string, Object>>>

Queries the dynamic intent entity information of an application based on [QueryParam](#queryparam). This API uses a promise to return the result asynchronously.<br/>If the user ID of the calling application is different from the target user ID, the permission `ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS` is required.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.EXECUTE_INSIGHT_INTENT

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| param | [QueryParam](#queryparam) | Yes | Intent entity parameters, which describe the query conditions of the intent entity and are used to query the intent entities that meet the conditions in the application. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<Array\<Record\<string, Object>>> | Promise object that returns the array of intent entities returned by the application. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 16000006 | Cross-user operations are not allowed. |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

**Example**

```ts
import { insightIntent, insightIntentDriver } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

function queryEntityInfoByPromise() {
  let queryParam: insightIntentDriver.QueryParam = {
    bundleName: 'com.example.intent', // Modify it to the actual bundle name.
    moduleName: 'entry', // Modify it to the actual module name.
    intentName: 'PlayMusic', // Modify it to the actual intent name.
    className: 'AppIntentEntityImpl', // Modify it to the actual class name.
    queryEntityParam: {
      queryType: insightIntent.QueryType.BY_PROPERTY,
      parameters: { // Modify it to the actual query parameters.
        'entityId': 'default'
      },
    },
    userId: 100,
  }

  try {
    insightIntentDriver.queryEntityInfo(queryParam)
      .then((data: Array<Record<string, Object>> | undefined) => {
        if (data) {
          hilog.info(0x0000, 'testTag', 'queryEntityInfo return %{public}s', JSON.stringify(data));
        } else {
          hilog.info(0x0000, 'testTag', 'queryEntityInfo return empty result');
        }
      })
      .catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', 'queryEntityInfo errCode: %{public}d', err.code);
        hilog.error(0x0000, 'testTag', 'queryEntityInfo errMessage %{public}s', err.message);
      });
  } catch (error) {
    hilog.error(0x0000, 'testTag', 'queryEntityInfo error caught %{public}s', JSON.stringify(error));
  }
}
```
