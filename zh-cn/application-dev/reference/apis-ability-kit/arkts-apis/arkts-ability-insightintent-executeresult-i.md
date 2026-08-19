# ExecuteResult

意图执行的返回结果。

**起始版本：** 23

<!--Device-insightIntent-interface ExecuteResult--><!--Device-insightIntent-interface ExecuteResult-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
import { insightIntentDriver } from '@kit.AbilityKit';
import { insightIntentProvider } from '@kit.AbilityKit';
```

## code

```TypeScript
code: int
```

意图执行返回的错误码，由开发者定义。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ExecuteResult-code: int--><!--Device-ExecuteResult-code: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## flags

```TypeScript
flags?: int
```

意图执行返回给系统入口的URI列表的授权权限。 **说明：** 该参数仅支持FLAG_AUTH_READ_URI_PERMISSION、FLAG_AUTH_WRITE_URI_PERMISSION、FLAG_AUTH_READ_URI_PERMISSION| FLAG_AUTH_WRITE_URI_PERMISSION。权限介绍见[Flags](arkts-ability-wantconstant-flags-e.md)。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ExecuteResult-flags?: int--><!--Device-ExecuteResult-flags?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## result

```TypeScript
result?: Record<string, RecordData>
```

Indicates execute result.

**类型：** Record&lt;string, [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecuteResult-result?: Record<string, RecordData>--><!--Device-ExecuteResult-result?: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uris

```TypeScript
uris?: Array<string>
```

意图执行返回的URI列表。该字段需要与flags字段配合使用，根据URI列表将flags字段的相应权限授权给系统入口。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ExecuteResult-uris?: Array<string>--><!--Device-ExecuteResult-uris?: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

