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

## ExecToolParam

CLI工具执行参数，用于拦截Hook。包含工具名称、子命令、参数、权限ticket字符串和执行选项。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

| 名称        | 类型 | 必填 | 说明 |
| ----------- | ---- | --- | ------------------ |
| toolName    | string | 是 | 工具名称。 |
| subCommand  | string | 是 | 子命令名称。 |
| args        | Record\<string, Object\> | 是 | 工具执行参数。 |
| challenge   | string | 是 | 使用[requestToolPermissions](js-apis-abilityToolAccessCtrl-sys.md#abilitytoolaccessctrlrequesttoolpermissions)接口生成的[TicketInfo](js-apis-abilityToolAccessCtrl-sys.md#ticketinfo)中的ticket字符串。 |
| execOptions | [ExecOptions](#execoptions) | 否 | 执行选项。<br/>默认值：详见[ExecOptions](#execoptions)的具体属性默认值。 |

## ExecCmdParam

Shell命令执行参数，用于拦截Hook。包含命令字符串和执行选项。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

| 名称           | 类型 | 必填 | 说明 |
| -------------- | ---- | --- | ------------------ |
| cmd            | string | 是 | 要执行的Shell命令。 |
| execCmdOptions | [ExecCmdOptions](js-apis-app-cli-cliManager.md#execcmdoptions) | 否 | 命令执行选项。<br/>默认值：详见[ExecCmdOptions](js-apis-app-cli-cliManager.md#execcmdoptions)的具体属性默认值。 |

## ExecResultWrap

执行结果包装类，用于[onAfterCallTool()](#onaftercalltool)和[onAfterCallCmd()](#onaftercallcmd)回调。包含执行结果。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

| 名称        | 类型 | 必填 | 说明 |
| ----------- | ---- | --- | ------------------ |
| execResult  | [ExecResult](js-apis-app-cli-cliManager.md#execresult) | 是 | 工具或命令的执行结果，包含退出码（exitCode）、标准输出（outputText）、标准错误输出（errorText）、终止信号（signalNumber）、是否超时（timeOut）和执行时长（executionTime），详见[ExecResult](js-apis-app-cli-cliManager.md#execresult)。在[onAfterCallTool()](#onaftercalltool)和[onAfterCallCmd()](#onaftercallcmd)回调中可读取该字段查看原始执行结果，修改后会将替换后的结果返回给调用方。 |

## CliHook

CLI工具和命令执行拦截Hook接口。Hook对象可实现该接口中可选方法的任意子集，仅已实现的方法会被调用，未实现的方法将被跳过。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

### onBeforeCallTool

onBeforeCallTool(param: ExecToolParam): ExecToolParam

工具执行前的回调。返回的对象将替换原始参数。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| param | [ExecToolParam](#exectoolparam) | 是 | 原始工具执行参数。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [ExecToolParam](#exectoolparam) | 替换后的工具执行参数。 |

**示例：**

```ts
import { CliHook, ExecToolParam } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const LOG_DOMAIN = 0x00;
const LOG_TAG = 'testTag';

const cliHook: CliHook = {
  onBeforeCallTool: (param: ExecToolParam): ExecToolParam => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onBeforeCallTool, toolName: ' + param.toolName);
    // 可在此修改执行参数，例如替换toolName或args
    return param;
  }
};
```

### onAfterCallTool

onAfterCallTool(param: ExecResultWrap): ExecResultWrap

工具执行后的回调。返回的对象将替换原始结果。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| param | [ExecResultWrap](#execresultwrap) | 是 | 原始工具执行结果。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [ExecResultWrap](#execresultwrap) | 修改后的工具执行结果。 |

**示例：**

```ts
import { CliHook, ExecResultWrap } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const LOG_DOMAIN = 0x00;
const LOG_TAG = 'testTag';

const cliHook: CliHook = {
  onAfterCallTool: (param: ExecResultWrap): ExecResultWrap => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onAfterCallTool, exitCode: ' + param.execResult.exitCode);
    // 可在此修改执行结果，例如改写stdout或exitCode
    return param;
  }
};
```

### onBeforeCallCmd

onBeforeCallCmd(param: ExecCmdParam): ExecCmdParam

命令执行前的回调。返回的对象将替换原始参数。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| param | [ExecCmdParam](#execcmdparam) | 是 | 原始命令执行参数。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [ExecCmdParam](#execcmdparam) | 替换后的命令执行参数。 |

**示例：**

```ts
import { CliHook, ExecCmdParam } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const LOG_DOMAIN = 0x00;
const LOG_TAG = 'testTag';

const cliHook: CliHook = {
  onBeforeCallCmd: (param: ExecCmdParam): ExecCmdParam => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onBeforeCallCmd, cmd: ' + param.cmd);
    // 可在此修改命令参数，例如替换cmd
    return param;
  }
};
```

### onAfterCallCmd

onAfterCallCmd(param: ExecResultWrap): ExecResultWrap

命令执行后的回调。返回的对象将替换原始结果。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| param | [ExecResultWrap](#execresultwrap) | 是 | 原始命令执行结果。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [ExecResultWrap](#execresultwrap) | 修改后的命令执行结果。 |

**示例：**

```ts
import { CliHook, ExecResultWrap } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const LOG_DOMAIN = 0x00;
const LOG_TAG = 'testTag';

const cliHook: CliHook = {
  onAfterCallCmd: (param: ExecResultWrap): ExecResultWrap => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onAfterCallCmd, exitCode: ' + param.execResult.exitCode);
    // 可在此修改命令结果，例如改写stdout或exitCode
    return param;
  }
};
```

## cliManager.registerCliHook

registerCliHook(hook: CliHook): Promise\<void\>

注册[CliHook](#clihook)。CliHook注册后用于拦截对[execTool()](#climanagerexectool)和[execCmd()](js-apis-app-cli-cliManager.md#climanagerexeccmd)的调用。本接口仅在开发者模式下可用。

同一时间只允许注册一个CLI Hook，已有Hook注册时再次注册将失败，如需更新已注册的Hook，请先调用[unregisterCliHook()](#climanagerunregisterclihook)取消注册后再重新注册。传入的Hook对象必须实现[CliHook](#clihook)接口中至少一个可选方法。

需要注意的是，注册CLI Hook的应用与调用[execTool()](#climanagerexectool)或[execCmd()](js-apis-app-cli-cliManager.md#climanagerexeccmd)的应用不能为同一应用：因为execTool()和execCmd()会同步阻塞主线程，而Hook回调同样在主线程执行，若为同一应用将因主线程被占用导致Hook回调无法触发。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.REGISTER_AGENT_HOOK

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| hook | [CliHook](#clihook) | 是 | 实现CliHook接口的Hook对象。该对象必须实现至少一个可选方法。 |

**返回值：**

| 类型           | 说明                     |
| -------------- | ------------------------ |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 35600034 | The device is not in developer mode.                         |
| 35600035 | A hook is already registered; unregister it first.           |
| 35600050 | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const LOG_DOMAIN = 0x00;
const LOG_TAG = 'testTag';

// 定义CLI Hook对象
const cliHook: CliHook = {
  onBeforeCallTool: (param: ExecToolParam): ExecToolParam => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onBeforeCallTool, toolName: ' + param.toolName);
    // 可在此修改执行参数
    return param;
  },
  onAfterCallTool: (param: ExecResultWrap): ExecResultWrap => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onAfterCallTool, exitCode: ' + param.execResult.exitCode);
    // 可在此修改执行结果
    return param;
  },
  onBeforeCallCmd: (param: ExecCmdParam): ExecCmdParam => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onBeforeCallCmd, cmd: ' + param.cmd);
    // 可在此修改命令参数
    return param;
  },
  onAfterCallCmd: (param: ExecResultWrap): ExecResultWrap => {
    hilog.info(LOG_DOMAIN, LOG_TAG, 'onAfterCallCmd, exitCode: ' + param.execResult.exitCode);
    // 可在此修改命令结果
    return param;
  }
};

export default class CliHookTest {
  static async registerHook() {
    try {
      // 注册CLI Hook
      await cliManager.registerCliHook(cliHook);
      hilog.info(LOG_DOMAIN, LOG_TAG, 'registerCliHook success.');
    } catch (error) {
      hilog.error(LOG_DOMAIN, LOG_TAG, `registerCliHook failed, errorCode: ${error.code}, message: ${error.message}`);
    }
  }
}
```

## cliManager.unregisterCliHook

unregisterCliHook(hook: CliHook): Promise\<void\>

取消注册已注册的CLI Hook。传入的Hook对象必须与调用[registerCliHook()](#climanagerregisterclihook)时传入的对象相同。若无Hook注册，调用将失败。

**起始版本：** 26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.REGISTER_AGENT_HOOK

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| hook | [CliHook](#clihook) | 是 | 要取消注册的Hook对象。 |

**返回值：**

| 类型           | 说明                     |
| -------------- | ------------------------ |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 35600036 | No hook is registered; nothing to unregister.               |
| 35600050 | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { cliManager, CliHook, ExecToolParam } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const LOG_DOMAIN = 0x00;
const LOG_TAG = 'testTag';

// cliHook为调用registerCliHook时传入的Hook对象
const cliHook: CliHook = {
  onBeforeCallTool: (param: ExecToolParam): ExecToolParam => {
    return param;
  }
};

export default class CliHookTest {
  static async unregisterHook() {
    try {
      // 取消注册CLI Hook
      await cliManager.unregisterCliHook(cliHook);
      hilog.info(LOG_DOMAIN, LOG_TAG, 'unregisterCliHook success.');
    } catch (error) {
      hilog.error(LOG_DOMAIN, LOG_TAG, `unregisterCliHook failed, errorCode: ${error.code}, message: ${error.message}`);
    }
  }
}
```
