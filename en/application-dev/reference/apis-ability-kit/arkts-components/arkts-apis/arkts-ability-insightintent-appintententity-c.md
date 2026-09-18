# AppIntentEntity

Define AppIntentEntity.

**Inheritance/Implementation:** AppIntentEntity implements [IntentEntity](arkts-ability-insightintent-intententity-i.md)

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## onQueryEntity

```TypeScript
abstract onQueryEntity(params: QueryEntityParam): Promise<Array<T>>
```

Called when query entity execute.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [QueryEntityParam](arkts-ability-insightintent-queryentityparam-i.md) | Yes | The params of query entity. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;T&gt;&gt; | Returns an array of subclasses of the AppIntentEntity class, support promise. |

**Examples**

```TypeScript
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

## displayName

```TypeScript
displayName: string
```

The display name of entity.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
