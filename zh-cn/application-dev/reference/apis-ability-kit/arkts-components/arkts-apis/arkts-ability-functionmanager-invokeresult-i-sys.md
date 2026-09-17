# InvokeResult（系统接口）

Function调用的结果。包含Function调用成功时返回的数据，调用失败时的错误码和错误信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { functionManager } from '@kit.AbilityKit';
```

## data

```TypeScript
data?: any
```

调用成功时返回的数据，类型可以为任意JSON值。仅在success为true时有值。默认值：undefined。

**类型：** any

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## errorCode

```TypeScript
errorCode?: number
```

调用失败时的错误码。仅在success为false时有值。默认值：undefined。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## errorMsg

```TypeScript
errorMsg?: string
```

调用失败时的错误描述。仅在success为false时有值。默认值：undefined。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## success

```TypeScript
success: boolean
```

调用是否成功（业务逻辑层面）。true：调用成功，data字段包含返回数据；false：调用失败，errorCode和errorMsg字段包含错误信息。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
