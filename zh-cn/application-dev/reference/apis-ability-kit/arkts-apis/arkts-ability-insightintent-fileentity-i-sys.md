# FileEntity（系统接口）

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

## flags

```TypeScript
flags?: number
```

要授予URI列表的权限。

**注意**

该参数只支持“FLAG_AUTH_READ_URI_PERMISSION”、“FLAG_AUTH_WRITE_URI_PERMISSION”、“标志位认证读URI”和“FLAG_AUTH_READ_URI_PERMISSION”和“FLAG_AUTH_WRITE_URI_PERMISSION”。权限说明请参见[标志](arkts-ability-wantconstant-flags-e.md)。取值限定为整数。

**类型：** number

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileEntity-flags?: int--><!--Device-FileEntity-flags?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
