# @ohos.app.cli.cliManager (CLI工具管理)(系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

本模块提供与系统命令行工具（CLI）的交互能力，可以查询工具信息、执行CLI命令。

**起始版本：** 26.0.0

> **说明：**
>
> 当前页面仅包含本模块的系统接口，其他公共接口参见[@ohos.app.cli.cliManager (CLI工具管理)](js-apis-app-cli-cliManager.md)。

## 导入模块

```ts
import { cliManager } from '@kit.AbilityKit';
```

## ExecOptions

执行CLI工具的可选参数。可用于指定CLI工具后台运行、前台执行时长、超时时长。

**起始版本：** 26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

| 名称       | 类型 | 必填 | 说明 |
| ---------- | ---- | --- | ------------------ |
| background | boolean | 否 | 表示任务是否后台执行。<br/>true：后台执行，false：前台执行。<br/>默认值：false。 |
| yieldMs    | number | 否 | 任务前台执行时长。取值范围：0 ~ 1000 * timeout。默认值：0。单位：ms。 |
| timeout    | number | 否 | 任务执行超时时长。取值范围：0 ~ 1800。默认值：1800。单位：s。 |

## cliManager.queryToolSummaries

queryToolSummaries(): Promise\<Array\<ToolSummary>>

查询所有CLI工具的摘要信息。摘要信息仅包含名称、版本和描述字段，使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.QUERY_CLI_TOOL

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**返回值：**

| 类型                               | 说明                       |
| ---------------------------------- | -------------------------- |
| Promise\<Array\<[ToolSummary](js-apis-inner-application-ToolInfo-sys.md#toolsummary)>> | Promise对象，返回工具摘要信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied, interface caller does not have permission "ohos.permission.QUERY_CLI_TOOL". |
| 202      | Not system application. Interface caller is not a system app. |
| 35600050 | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { cliManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 查询所有CLI工具的摘要信息
  cliManager.queryToolSummaries().then((toolSummaries) => {
    hilog.info(0x0000, 'CliManager', 'queryToolSummaries success, count: %{public}d', toolSummaries.length);
    for (const summary of toolSummaries) {
      hilog.info(0x0000, 'CliManager', 'Tool name: %{public}s, version: %{public}s', summary.name, summary.version);
    }
  }).catch((error: BusinessError) => {
    hilog.error(0x0000, 'CliManager', 'queryToolSummaries failed, code: %{public}d, message: %{public}s',
      error.code, error.message);
  });
} catch (error) {
  hilog.error(0x0000, 'CliManager', 'queryToolSummaries failed, error: %{public}s', JSON.stringify(error));
}
```

## cliManager.queryTools

queryTools(): Promise\<Array\<ToolInfo\>\>

查询所有CLI工具的详细信息，使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.QUERY_CLI_TOOL

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**返回值：**

| 类型                               | 说明                       |
| ---------------------------------- | -------------------------- |
| Promise\<Array\<[ToolInfo](js-apis-inner-application-ToolInfo-sys.md#toolinfo)\>\> | Promise对象，返回工具详细信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied, interface caller does not have permission "ohos.permission.QUERY_CLI_TOOL". |
| 202      | Not system application. Interface caller is not a system app. |
| 35600050 | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { cliManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 查询所有CLI工具的详细信息
  cliManager.queryTools().then((toolInfos) => {
    hilog.info(0x0000, 'CliManager', 'queryTools success, count: %{public}d', toolInfos.length);
    for (const toolInfo of toolInfos) {
      hilog.info(0x0000, 'CliManager', 'Tool name: %{public}s, version: %{public}s', toolInfo.name, toolInfo.version);
    }
  }).catch((error: BusinessError) => {
    hilog.error(0x0000, 'CliManager', 'queryTools failed, code: %{public}d, message: %{public}s',
      error.code, error.message);
  });
} catch (error) {
  hilog.error(0x0000, 'CliManager', 'queryTools failed, error: %{public}s', JSON.stringify(error));
}
```

## cliManager.getToolInfoByName

getToolInfoByName(toolName: string): Promise\<ToolInfo\>

根据工具名称获取单个工具的详细信息，使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.QUERY_CLI_TOOL

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名   | 类型   | 必填 | 说明               |
| -------- | ------ | ---- | ------------------ |
| toolName | string | 是   | 目标工具的名称。 |

**返回值：**

| 类型                                         | 说明                               |
| -------------------------------------------- | ---------------------------------- |
| Promise\<[ToolInfo](js-apis-inner-application-ToolInfo-sys.md#toolinfo)> | Promise对象，返回工具的详细信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied, interface caller does not have permission "ohos.permission.QUERY_CLI_TOOL". |
| 202      | Not system application. Interface caller is not a system app. |
| 35600030 | No tool with the specified name exists.                      |
| 35600050 | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { cliManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let toolName = 'example_tool';
try {
  // 根据工具名称获取工具的详细信息
  cliManager.getToolInfoByName(toolName).then((toolInfo) => {
    hilog.info(0x0000, 'CliManager', 'getToolInfoByName success, name: %{public}s', toolInfo.name);
  }).catch((error: BusinessError) => {
    hilog.error(0x0000, 'CliManager', 'getToolInfoByName failed, code: %{public}d, message: %{public}s',
      error.code, error.message);
  });
} catch (error) {
  hilog.error(0x0000, 'CliManager', 'getToolInfoByName failed, error: %{public}s', JSON.stringify(error));
}
```

## cliManager.execTool
execTool(toolName: string, subCommand: string, args: Record\<string, Object\>, challenge: string, execOptions?: ExecOptions): Promise\<CliSessionInfo\>

执行CLI命令，返回会话信息。

**起始版本：** 26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.EXEC_CLI_TOOL

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| toolName | string | 是 | CLI工具名称。 |
| subCommand | string | 是 | CLI工具子命令名称。如果没有子命令则填空串。 |
| args | Record\<string, Object\> | 是 | 命令执行的参数。 |
| challenge | string | 是 | 使用[requestToolPermissions](js-apis-abilityToolAccessCtrl-sys.md#abilitytoolaccessctrlrequesttoolpermissions)接口生成的[TicketInfo](js-apis-abilityToolAccessCtrl-sys.md#ticketinfo)中的ticket字符串。 |
| execOptions | [ExecOptions](#execoptions) | 否 | 执行命令的可选参数。默认值：详见[ExecOptions](#execoptions)的具体属性默认值。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<[CliSessionInfo](js-apis-app-cli-cliManager.md#clisessioninfo)\> | Promise对象。返回会话信息。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied, interface caller does not have permission "ohos.permission.EXEC_CLI_TOOL". |
| 202 | Not system application. Interface caller is not a system app. |
| 35600030 | No tool with the specified name exists. |
| 35600031 | Maximum number of processes has been reached. |
| 35600050  | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { abilityToolAccessCtrl, cliManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 定义CLI命令信息
let cliCmdInfo: abilityToolAccessCtrl.CliCmdInfo = {
  cliCmdName: 'ohos-aa',
  subCliCmdName: 'start'
};
let cliOp: abilityToolAccessCtrl.OperationInfo = {
  operationType: abilityToolAccessCtrl.OperationType.CLI,
  info: cliCmdInfo
};
let permissionQuery: abilityToolAccessCtrl.PermissionQuery = {
  operationInfo: [cliOp],
  needTicket: true,
  ticketExpireTimeMs: 10000
};
try {
  // 查询工具权限并获取ticket
  const res = await abilityToolAccessCtrl.requestToolPermissions(permissionQuery);
  let command: string = 'ohos-aa';
  let curArgs: Record<string, Object> = {
    'bundlename': 'com.example.myapplication',
    'abilityname': 'EntryAbility'
  };
  let subCommand: string = 'start';
  let curOptions: cliManager.ExecOptions = {
    background: false,
    yieldMs: 5000,
    timeout: 5
  };
  // 执行CLI命令
  let curSessionInfo: cliManager.CliSessionInfo =
    await cliManager.execTool(command, subCommand, curArgs, res.ticket?.ticket, curOptions);
  hilog.info(0x0000, 'CliManager', 'execTool result=%{public}s', JSON.stringify(curSessionInfo));
} catch (err) {
  let error = err as BusinessError;
  hilog.error(0x0000, 'CliManager', 'execTool error, code: %{public}d, message: %{public}s',
    error.code, error.message);
}
```

