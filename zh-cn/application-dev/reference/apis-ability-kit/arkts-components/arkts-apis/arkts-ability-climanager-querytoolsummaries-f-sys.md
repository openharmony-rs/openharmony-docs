# queryToolSummaries（系统接口）

## 导入模块

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## queryToolSummaries

```TypeScript
function queryToolSummaries(): Promise<Array<ToolSummary>>
```

查询所有CLI工具的摘要信息。摘要信息仅包含名称、版本和描述字段，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.QUERY_CLI_TOOL

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[ToolSummary](arkts-ability-toolinfo-toolsummary-i-sys.md)&gt;&gt; | Promise对象，返回工具摘要信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, interface caller does not have permission"ohos.permission.QUERY_CLI_TOOL". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. Interface caller is not a system app. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
