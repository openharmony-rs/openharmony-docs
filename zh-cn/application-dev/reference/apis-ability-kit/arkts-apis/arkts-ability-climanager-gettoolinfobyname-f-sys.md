# getToolInfoByName（系统接口）

## 导入模块

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## getToolInfoByName

```TypeScript
function getToolInfoByName(toolName: string): Promise<ToolInfo>
```

根据工具名称获取单个工具的详细信息，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.QUERY_CLI_TOOL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-cliManager-function getToolInfoByName(toolName: string): Promise<ToolInfo>--><!--Device-cliManager-function getToolInfoByName(toolName: string): Promise<ToolInfo>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toolName | string | 是 | 目标工具的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ToolInfo](arkts-ability-toolinfo-i-sys.md)&gt; | Promise对象，返回工具的详细信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35600030](../errorcode-ability.md#35600030-cli工具不存在) | No tool with the specified name exists. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, interface caller does not have permission "ohos.permission.QUERY_CLI_TOOL". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. Interface caller is not a system app. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |

