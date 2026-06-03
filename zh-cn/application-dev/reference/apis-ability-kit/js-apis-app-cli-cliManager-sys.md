# @ohos.app.cli.cliManager (CLI工具管理)(系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @dsz2025-->
<!--Adviser: @HelloCrease-->

本模块提供与系统命令行工具（CLI）的交互能力，可以查询工具信息、调用并执行CLI命令，以及管理会话。

**起始版本：** 26.0.0

> **说明：**
>
> 本模块仅适用于ArkTS-Dyn。  
> 本模块接口为系统接口。

## 导入模块

```ts
import { cliManager } from '@kit.AbilityKit';
```

## cliManager.queryToolSummaries

queryToolSummaries(): Promise\<Array\<ToolSummary>>

查询所有CLI工具的摘要信息。摘要信息仅包含名称、版本和描述字段。

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

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Not system application.                                      |
| 35600050 | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { cliManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cliManager.queryToolSummaries().then((toolSummaries) => {
    console.info('queryToolSummaries success, count: ' + toolSummaries.length);
    for (const summary of toolSummaries) {
      console.info('Tool name: ' + summary.name + ', version: ' + summary.version);
    }
  }).catch((error: BusinessError) => {
    console.error('queryToolSummaries failed, error: ' + error.message);
  });
} catch (error) {
  console.error('queryToolSummaries failed, error: ' + JSON.stringify(error));
}
```

## cliManager.queryTools

queryTools(): Promise\<Array\<ToolInfo>>

查询所有CLI工具的详细信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.QUERY_CLI_TOOL

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**返回值：**

| 类型                               | 说明                       |
| ---------------------------------- | -------------------------- |
| Promise\<Array\<[ToolInfo](js-apis-inner-application-ToolInfo-sys.md#toolinfo)>> | Promise对象，返回工具详细信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Not system application.                                      |
| 35600050 | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { cliManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cliManager.queryTools().then((toolInfos) => {
    console.info('queryTools success, count: ' + toolInfos.length);
    for (const toolInfo of toolInfos) {
      console.info('Tool name: ' + toolInfo.name + ', version: ' + toolInfo.version);
    }
  }).catch((error: BusinessError) => {
    console.error('queryTools failed, error: ' + error.message);
  });
} catch (error) {
  console.error('queryTools failed, error: ' + JSON.stringify(error));
}
```

## cliManager.getToolInfoByName

getToolInfoByName(toolName: string): Promise\<ToolInfo>

根据工具名称获取单个工具的详细信息。

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

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Not system application.                                      |
| 35600030 | No tool with the specified name exists.                      |
| 35600050 | System Error. 1. Connect to system service failed; 2. System service failed to communicate with dependency module. |

**示例：**

```ts
import { cliManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let toolName = 'example_tool';
try {
  cliManager.getToolInfoByName(toolName).then((toolInfo) => {
    console.info('getToolInfoByName success, name: ' + toolInfo.name);
  }).catch((error: BusinessError) => {
    console.error('getToolInfoByName failed, error: ' + error.message);
  });
} catch (error) {
  console.error('getToolInfoByName failed, error: ' + JSON.stringify(error));
}
```

