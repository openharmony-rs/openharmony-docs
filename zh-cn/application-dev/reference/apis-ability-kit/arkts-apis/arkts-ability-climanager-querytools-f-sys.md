# queryTools（系统接口）

## 导入模块

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## queryTools

```TypeScript
function queryTools(): Promise<Array<ToolInfo>>
```

查询所有CLI工具的详细信息，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.QUERY_CLI_TOOL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-cliManager-function queryTools(): Promise<Array<ToolInfo>>--><!--Device-cliManager-function queryTools(): Promise<Array<ToolInfo>>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[ToolInfo](arkts-ability-toolinfo-i-sys.md)&gt;&gt; | Promise对象，返回工具详细信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, interface caller does not have permission "ohos.permission.QUERY_CLI_TOOL". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. Interface caller is not a system app. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |

