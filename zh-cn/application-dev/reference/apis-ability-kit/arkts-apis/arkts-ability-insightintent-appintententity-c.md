# AppIntentEntity

```TypeScript
abstract class AppIntentEntity<T> implements IntentEntity
```

定义AppIntentEntity。

**继承/实现关系：** AppIntentEntity implements [IntentEntity](arkts-ability-insightintent-intententity-i.md)

**起始版本：** 26.0.0

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

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [QueryEntityParam](arkts-ability-insightintent-queryentityparam-i.md) | 是 | 查询实体的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;T&gt;&gt; | Returns an array of subclasses of the AppIntentEntity class, support promise. |

**示例**

## displayName

```TypeScript
displayName: string
```

实体的显示名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
