# @ohos.app.ability.insightIntent (Basic Definitions of InsightIntent Framework)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=4a5664ccf73fb25c25f374f85b4ad06104beeb9a translatedAt=2026-09-03T10:18:57.344Z pushedAt=2026-09-05T10:47:30.396Z -->

This module provides basic definitions of the [InsightIntent framework](../../application-models/insight-intent-overview.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { insightIntent } from '@kit.AbilityKit';
```

## ExecuteMode

Enumerates the intent execution modes. It specifies the mode of execution passed when the intent is triggered by a system entry point. The supported execution modes for each intent are defined during intent development.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Value| Description|
| -------- | -------- | -------- |
| UI_ABILITY_FOREGROUND | 0 | Display a UIAbility in the foreground.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| UI_ABILITY_BACKGROUND | 1 | Start a UIAbility in the background.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| UI_EXTENSION_ABILITY | 2 | Start a UIExtensionAbility.|

## ExecuteResult

Enumerates the return results of intent execution.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| code | number | No| No| Error code returned by the intent execution, defined by the developer.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| result | Record<string, Object> | No| Yes| Result data returned by the intent execution, typically containing information to be passed back to the system entry point.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| uris<sup>18+</sup> | Array&lt;string&gt; | No| Yes| List of URIs returned by the intent execution. This field must be used together with the **flags** field to grant the corresponding permissions for the URI list to the system entry point.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| flags<sup>18+</sup> | number | No| Yes| Permissions to be granted to the system entry point for the URI list returned by the intent execution.<br>**Atomic service API**: This API can be used in atomic services since API version 18.<br>**NOTE**<br>This parameter supports only FLAG_AUTH_READ_URI_PERMISSION, FLAG_AUTH_WRITE_URI_PERMISSION, and FLAG_AUTH_READ_URI_PERMISSION\|FLAG_AUTH_WRITE_URI_PERMISSION. For details about the permissions, see [Flags](js-apis-app-ability-wantConstant.md#flags).|

## IntentEntity<sup>20+</sup>

Defines the struct of an intent entity. It represents key information objects involved during intent execution, including intent parameters and execution results.

You can define intent entities by inheriting this class. The child class must be decorated with [@InsightIntentEntity](./js-apis-app-ability-InsightIntentDecorator.md#insightintententity).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| entityId | string | No| No| ID of the intent entity.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## IntentResult\<T><sup>20+</sup>

Return result of intent execution, which supports [generic types](../../quick-start/arkts-language-guide-generics.md#generic-class).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| code | number | No| No| Error code returned by the intent execution, defined by the developer.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| result | T | No| Yes| Result data returned by the intent execution, typically containing information to be passed back to the system entry point.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## ReturnMode<sup>23+</sup>

Enumerates the modes that define how the execution result of an intent is returned to the intent initiator.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Value| Description|
| -------- | -------- | -------- |
| CALLBACK | 0 | The intent execution result is returned through the [onExecuteInUIAbilityForegroundMode](./js-apis-app-ability-insightIntentExecutor.md#onexecuteinuiabilityforegroundmode) or [onExecuteInUIExtensionAbility](./js-apis-app-ability-insightIntentExecutor.md#onexecuteinuiextensionability) API in the [intent execution base class](./js-apis-app-ability-insightIntentExecutor.md).<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| FUNCTION | 1 | The intent execution result is returned after the [sendExecuteResult](./js-apis-app-ability-insightIntentProvider.md#insightintentprovidersendexecuteresult) or [sendIntentResult](./js-apis-app-ability-insightIntentProvider.md#insightintentprovidersendintentresult) API in [intent provider management](./js-apis-app-ability-insightIntentProvider.md) is called.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|

## QueryType

Enumerates the query modes of intent entities.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

| Name | Value | Description |
| -------- | -------- | -------- |
| ALL | 'all' | Queries all intent entities. |
| BY_PROPERTY | 'byProperty' | Queries intent entities by the supportedQueryProperties attribute in [IntentEntityDecoratorInfo](./js-apis-app-ability-InsightIntentDecorator.md#intententitydecoratorinfo). |

## QueryEntityParam

Query parameters of the intent entity.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| queryType | [QueryType](#querytype) | No | No | Query mode of the intent entity. |
| parameters | Record\<string, Object> | No | Yes | Query parameters of the intent entity. This field is required when [QueryType](#querytype) is [BY_PROPERTY](#querytype). |

## AppIntentEntity

Defines an intent entity that supports querying data in an application. It inherits from [IntentEntity](#intententity20) and is used to define the information objects that an application needs to expose.

Developers define a queryable intent entity by inheriting from this class. The inherited class must be decorated with [@InsightIntentEntity](./js-apis-app-ability-InsightIntentDecorator.md#insightintententity).

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| displayName | string | No | No | Display name of the intent entity.<br/>**Atomic service API**: Since API version 26.0.0, this API is supported in atomic services. |

### onQueryEntity

abstract onQueryEntity(params: QueryEntityParam): Promise\<Array\<T>>

When a system entry triggers an intent entity query, the system loads this class and triggers this callback. In this callback, developers can implement the intent entity operation to be executed, and return the entity information that meets the conditions based on the input parameter [QueryEntityParam](#queryentityparam). A Promise is used to return the result asynchronously.<br/>It is recommended that all information of the intent entity be returned when [queryType](#querytype) is [ALL](#querytype), and that the information that meets the conditions be returned based on the property values in [parameters](#queryentityparam) when [queryType](#querytype) is [BY_PROPERTY](#querytype).

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| params | [QueryEntityParam](#queryentityparam) | Yes | Intent entity query parameter. |

**Return value**

| Type | Description |
|------|-----|
| Promise\<Array\<T>>| Promise object. Returns the Array\<T> object, which indicates the intent entity information that meets the conditions returned by the intent entity.|

**Example**

```ts
import { insightIntent, InsightIntentEntity } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@InsightIntentEntity({
  entityCategory: 'string_entity_category',
  parameters: {
    '$id': '/schemas/StringIntentEntity',
    'type': 'object',
    'description': 'String type intent entity with dynamic query',
    'properties': {
      'entityId': {
        'type': 'string',
        'description': 'Data unique identifier',
        'title': 'Unique identifier of the execution scenario.'
      },
      'name': {
        'type': 'string',
        'description': 'The name of string entity',
        'title': 'Name of the execution scenario.'
      },
      'extension': {
        'type': 'string',
        'description': 'The description of string entity value',
        'title': 'Extension field of the execution scenario.'
      },
      'displayName': {
        'type': 'string',
        'description': 'The display name of string entity',
      },
      'description': {
        'type': 'string',
        'description': 'The description of string entity value',
      }
    },
    'required': ['name', 'displayName']
  },
  supportedQueryProperties: ['entityId', 'name', 'extension'] // Indicates that onQueryEntity supports querying entity information by the entityId, name, or extension property.
})
export class AppIntentEntityImpl extends insightIntent.AppIntentEntity<AppIntentEntityImpl> {
  entityId: string = 'default';
  name: string = '';
  displayName: string = '';
  description?: string;
  extension?: string;

  async onQueryEntity(params: insightIntent.QueryEntityParam): Promise<Array<AppIntentEntityImpl>> {
    const appStringEntities: AppIntentEntityImpl[] = [
      this.createEntityInstance('id1', 'Name 1', 'Display name 1', 'Description 1', 'Extension field 1'),
      this.createEntityInstance('id2', 'Name 2', 'Display name 2', 'Description 2', 'Extension field 2'),
      this.createEntityInstance('id3', 'Name 3', 'Display name 3', 'Description 3', 'Extension field 3'),
    ];

    let resultEntities: AppIntentEntityImpl[] = [];
    const queryType = params.queryType;
    const parameters = params.parameters ?? {};
    switch (queryType) {
      case insightIntent.QueryType.ALL:
        resultEntities = appStringEntities;
        break;
      case insightIntent.QueryType.BY_PROPERTY:
        // 1. Verify whether parameters contains valid query keys (only keys in supportedQueryProperties are supported).
        const validQueryKeys = Object.keys(parameters).filter(key => (['entityId', 'name', 'extension'] as string[]).includes(key));
        if (validQueryKeys.length === 0) {
          hilog.error(0x0000, 'testTag', 'Query missing valid parameters, support: entityId/name/extension');
          resultEntities = [];
          break;
        }
        // 2. Perform multi-condition AND filtering on all valid query keys.
        resultEntities = appStringEntities.filter(entity => {
          return validQueryKeys.every(key => {
            const queryValue = parameters[key];
            if (key === 'entityId') {
              return entity.entityId === queryValue;
            } else if (key === 'name') {
              return entity.name === queryValue;
            } else if (key === 'extension') {
              return entity.extension === queryValue;
            }
            return false;
          });
        });
        break;
      default:
        resultEntities = [];
    }
    return resultEntities;
  }

  private createEntityInstance(entityId: string, name: string, displayName: string, description?: string, extension?: string): AppIntentEntityImpl {
    const instance = new AppIntentEntityImpl();
    instance.entityId = entityId;
    instance.name = name;
    instance.displayName = displayName;
    instance.description = description;
    instance.extension = extension;
    return instance;
  }
}
```
<!--no_check-->