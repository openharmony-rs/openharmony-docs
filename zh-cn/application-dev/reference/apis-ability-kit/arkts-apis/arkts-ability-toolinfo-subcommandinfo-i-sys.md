# SubCommandInfo（系统接口）

描述CLI工具子命令的信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## description

```TypeScript
readonly description: string
```

子命令的描述。应清晰说明该子命令的具体功能和使用场景。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## eventSchemas

```TypeScript
readonly eventSchemas?: Record<string, Record<string, Object>>
```

子命令自定义事件的模式定义。以键值对形式存储，键为事件类型，值为该事件的JSON Schema定义。默认值为空对象。

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

## inputSchema

```TypeScript
readonly inputSchema: Record<string, Object>
```

子命令的输入模式定义。使用JSON Schema格式定义输入参数的结构和类型。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## outputSchema

```TypeScript
readonly outputSchema: Record<string, Object>
```

子命令的输出模式定义。使用JSON Schema格式定义输出数据的结构和类型。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## requirePermissions

```TypeScript
readonly requirePermissions?: Array<string>
```

子命令所需的权限列表。所有权限项必须为唯一的字符串。系统将在执行该子命令时校验调用者是否具备所需权限，不具备相应权限将无法执行。默认值为空数组。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
