# FileEntity

```TypeScript
interface FileEntity extends IntentEntity
```

定义文件实体的结构体。表示意图执行过程中涉及的关键文件对象，包括意图参数和执行结果。

**继承/实现关系：** FileEntity extends [IntentEntity](arkts-ability-insightintent-intententity-i.md)

**起始版本：** 26.2.0

<!--Device-insightIntent-interface FileEntity extends IntentEntity--><!--Device-insightIntent-interface FileEntity extends IntentEntity-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## entityId

```TypeScript
entityId: 'OHOS_FILE_ENTITY'
```

文件实体标识。固定为'OHOS_FILE_ENTITY'。

**类型：** 'OHOS_FILE_ENTITY'

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-FileEntity-entityId: 'OHOS_FILE_ENTITY'--><!--Device-FileEntity-entityId: 'OHOS_FILE_ENTITY'-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uris

```TypeScript
uris: Array<string>
```

URI列表。

**类型：** Array&lt;string&gt;

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-FileEntity-uris: Array<string>--><!--Device-FileEntity-uris: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
