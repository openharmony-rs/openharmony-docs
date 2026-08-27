# ToolInfo（系统接口）

ToolInfo用于描述系统命令行工具（CLI）的基本信息，包括工具名称、版本、描述、可执行路径、输入输出模式等。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## description

```TypeScript
readonly description: string
```

CLI工具的功能描述。该描述应清晰说明工具的核心功能和用途，帮助用户理解工具能做什么。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## eventSchemas

```TypeScript
readonly eventSchemas?: Record<string, Record<string, Object>>
```

自定义事件的模式定义。以键值对形式存储，键为事件类型，值为该事件的JSON Schema定义。默认值为空对象。

**类型：** Record&lt;string, Record&lt;string, Object&gt;&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## eventTypes

```TypeScript
readonly eventTypes?: Array<string>
```

CLI工具支持的自定义事件类型列表。所有事件类型必须为唯一的字符串。默认值为空数组。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## executablePath

```TypeScript
readonly executablePath: string
```

CLI工具的可执行文件路径。必须是绝对路径。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## hasSubCommand

```TypeScript
readonly hasSubCommand?: boolean
```

指示该工具是否支持子命令。true表示工具支持子命令，false表示不支持子命令。默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## inputSchema

```TypeScript
readonly inputSchema: Record<string, Object>
```

CLI工具的输入模式定义。使用JSON Schema格式定义输入参数的结构和类型，用于描述工具接受的输入数据格式。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## isLockScreenExecutionAllowed

```TypeScript
readonly isLockScreenExecutionAllowed?: boolean
```

指示该工具是否支持在锁屏状态下执行。true表示工具支持在锁屏状态下执行，false表示工具不支持在锁屏状态下执行。默认值为false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## name

```TypeScript
readonly name: string
```

CLI工具的名称，用于在系统中唯一标识一个CLI工具。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## outputSchema

```TypeScript
readonly outputSchema: Record<string, Object>
```

CLI工具的输出模式定义。使用JSON Schema格式定义输出数据的结构和类型，用于描述工具返回的输出数据格式。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## requirePermissions

```TypeScript
readonly requirePermissions?: Array<string>
```

CLI工具所需的权限列表。所有权限项必须为唯一的字符串。系统将在执行该工具时校验调用者是否具备所需权限，不具备相应权限将无法执行。默认值为空数组。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## subcommands

```TypeScript
readonly subcommands?: Record<string, SubCommandInfo>
```

子命令信息列表。以键值对形式存储，键为子命令名称，值为子命令的详细信息。默认值为空对象。

**类型：** Record&lt;string, [SubCommandInfo](arkts-ability-toolinfo-subcommandinfo-i-sys.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## version

```TypeScript
readonly version: string
```

CLI工具的版本号。遵循语义化版本规范（如"1.0.0"），格式由提供商定义。版本号用于标识工具的功能迭代和兼容性变化。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
