# ExecuteResult

ArkTS脚本执行结果。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-scriptManager-interface ExecuteResult--><!--Device-scriptManager-interface ExecuteResult-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## code

```TypeScript
code: number
```

表示结果码。取值范围为整数，默认值为0。

**类型：** number

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExecuteResult-code: number--><!--Device-ExecuteResult-code: number-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## flags

```TypeScript
flags?: number
```

表示URI的读写权限，与flags的flags字段含义一致。取值范围如下： FLAG_AUTH_READ_URI_PERMISSION：读权限。 FLAG_AUTH_WRITE_URI_PERMISSION：写权限。 以上两个标志的组合：同时授权读写权限。

**类型：** number

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExecuteResult-flags?: number--><!--Device-ExecuteResult-flags?: number-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## result

```TypeScript
result?: Record<string, Object>
```

表示脚本执行结果。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExecuteResult-result?: Record<string, Object>--><!--Device-ExecuteResult-result?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## uris

```TypeScript
uris?: Array<string>
```

表示需要授权给调用方的URI列表。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExecuteResult-uris?: Array<string>--><!--Device-ExecuteResult-uris?: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

