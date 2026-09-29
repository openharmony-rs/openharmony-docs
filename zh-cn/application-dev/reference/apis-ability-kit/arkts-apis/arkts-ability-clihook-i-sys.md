# CliHook（系统接口）

```TypeScript
export interface CliHook
```

用于拦截CLI工具和命令执行的Hook接口。

Hook对象可实现可选方法的任意子集。仅已实现的方法会被调用；未实现的方法将被跳过。

**起始版本：** 26.0.1

<!--Device-unnamed-export interface CliHook--><!--Device-unnamed-export interface CliHook-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## onAfterCallCmd

```TypeScript
onAfterCallCmd?(param: ExecResultWrap): ExecResultWrap
```

命令执行后调用。返回的对象将替换原始结果。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliHook-onAfterCallCmd?(param: ExecResultWrap): ExecResultWrap--><!--Device-CliHook-onAfterCallCmd?(param: ExecResultWrap): ExecResultWrap-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [ExecResultWrap](arkts-ability-clihook-execresultwrap-i-sys.md) | 是 | 执行结果参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ExecResultWrap](arkts-ability-clihook-execresultwrap-i-sys.md) | 返回（可能已被修改的）结果参数。 |

## onAfterCallTool

```TypeScript
onAfterCallTool?(param: ExecResultWrap): ExecResultWrap
```

工具执行后调用。返回的对象将替换原始结果。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliHook-onAfterCallTool?(param: ExecResultWrap): ExecResultWrap--><!--Device-CliHook-onAfterCallTool?(param: ExecResultWrap): ExecResultWrap-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [ExecResultWrap](arkts-ability-clihook-execresultwrap-i-sys.md) | 是 | 执行结果参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ExecResultWrap](arkts-ability-clihook-execresultwrap-i-sys.md) | 返回（可能已被修改的）结果参数。 |

## onBeforeCallCmd

```TypeScript
onBeforeCallCmd?(param: ExecCmdParam): ExecCmdParam
```

命令执行前调用。返回的对象将替换原始参数。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliHook-onBeforeCallCmd?(param: ExecCmdParam): ExecCmdParam--><!--Device-CliHook-onBeforeCallCmd?(param: ExecCmdParam): ExecCmdParam-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [ExecCmdParam](arkts-ability-clihook-execcmdparam-i-sys.md) | 是 | 原始命令执行参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ExecCmdParam](arkts-ability-clihook-execcmdparam-i-sys.md) | 返回（可能已被修改的）参数。 |

## onBeforeCallTool

```TypeScript
onBeforeCallTool?(param: ExecToolParam): ExecToolParam
```

工具执行前调用。返回的对象将替换原始参数。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliHook-onBeforeCallTool?(param: ExecToolParam): ExecToolParam--><!--Device-CliHook-onBeforeCallTool?(param: ExecToolParam): ExecToolParam-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [ExecToolParam](arkts-ability-clihook-exectoolparam-i-sys.md) | 是 | 原始工具执行参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ExecToolParam](arkts-ability-clihook-exectoolparam-i-sys.md) | 返回（可能已被修改的）参数。 |
