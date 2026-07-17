# AppIntentEntity

定义AppIntentEntity。

**继承/实现关系：** AppIntentEntity implements [IntentEntity](arkts-ability-insightintent-intententity-i.md)

**起始版本：** 26.0.0

<!--Device-insightIntent-abstract class AppIntentEntity<T> implements IntentEntity--><!--Device-insightIntent-abstract class AppIntentEntity<T> implements IntentEntity-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## onQueryEntity

```TypeScript
abstract onQueryEntity(params: QueryEntityParam): Promise<Array<T>>
```

在查询实体执行时调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AppIntentEntity-abstract onQueryEntity(params: QueryEntityParam): Promise<Array<T>>--><!--Device-AppIntentEntity-abstract onQueryEntity(params: QueryEntityParam): Promise<Array<T>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [QueryEntityParam](arkts-ability-insightintent-queryentityparam-i.md) | 是 | 查询实体的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<T>> | - Returns an array of subclasses of the AppIntentEntity class, support promise. |

**示例：**

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
        'title': '执行场景的唯一标识'
      },
      'name': {
        'type': 'string',
        'description': 'The name of string entity',
        'title': '执行场景的名称'
      },
      'extension': {
        'type': 'string',
        'description': 'The description of string entity value',
        'title': '执行场景的扩展字段'
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
  supportedQueryProperties: ['entityId', 'name', 'extension'] // 表示onQueryEntity支持通过entityId、name或者extension属性来查询实体信息
})
export class AppIntentEntityImpl extends insightIntent.AppIntentEntity<AppIntentEntityImpl> {
  entityId: string = 'default';
  name: string = '';
  displayName: string = '';
  description?: string;
  extension?: string;

  async onQueryEntity(params: insightIntent.QueryEntityParam): Promise<Array<AppIntentEntityImpl>> {
    const appStringEntities: AppIntentEntityImpl[] = [
      this.createEntityInstance('id1', '名称1', '显示名称1', '描述1', '扩展字段1'),
      this.createEntityInstance('id2', '名称2', '显示名称2', '描述2', '扩展字段2'),
      this.createEntityInstance('id3', '名称3', '显示名称3', '描述3', '扩展字段3'),
    ];

    let resultEntities: AppIntentEntityImpl[] = [];
    const queryType = params.queryType;
    const parameters = params.parameters ?? {};
    switch (queryType) {
      case insightIntent.QueryType.ALL:
        resultEntities = appStringEntities;
        break;
      case insightIntent.QueryType.BY_PROPERTY:
        // 1. 校验parameters是否有有效的查询键（仅支持supportedQueryProperties中的键）
        const validQueryKeys = Object.keys(parameters).filter(key => (['entityId', 'name', 'extension'] as string[]).includes(key));
        if (validQueryKeys.length === 0) {
          hilog.error(0x0000, 'testTag', 'Query missing valid parameters, support: entityId/name/extension');
          resultEntities = [];
          break;
        }
        // 2. 对所有有效查询键做多条件 AND 过滤
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

实体的显示名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AppIntentEntity-displayName: string--><!--Device-AppIntentEntity-displayName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

