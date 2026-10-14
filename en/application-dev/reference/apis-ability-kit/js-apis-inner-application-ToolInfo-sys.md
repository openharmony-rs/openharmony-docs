# ToolInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @dsz2025-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=9b45198dbdb6f53f8bf0896d62425626f2442690 translatedAt=2026-09-03T12:04:57.175Z pushedAt=2026-09-05T10:47:30.871Z -->

ToolInfo describes the basic information about a system command-line tool (CLI), including the tool name, version, description, executable path, input/output mode, and so on.

**Since:** 26.0.0

> **NOTE**
>
> The APIs of this module are system APIs.

## Modules to Import

```ts
import { ToolInfo, ToolSummary, SubCommandInfo } from '@kit.AbilityKit';
```

## ToolInfo

Describes the basic information about a CLI tool.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

| Name               | Type                                                   | Read-only | Optional | Description                                                         |
| ------------------ | ------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| name               | string                                                 | Yes   | No   | Name of the CLI tool, used to uniquely identify a CLI tool in the system.        |
| version            | string                                                 | Yes   | No   | Version number of the CLI tool. It follows the semantic versioning specification (for example, "1.0.0"), and the format is defined by the provider. The version number is used to identify the feature iteration and compatibility changes of the tool. |
| description        | string                                                 | Yes   | No   | Functional description of the CLI tool. The description should clearly explain the core functions and purpose of the tool to help users understand what the tool can do. |
| executablePath     | string                                                 | Yes   | No   | Path of the executable file of the CLI tool. It must be an absolute path.                    |
| requirePermissions | Array\<string>                                         | Yes   | Yes   | List of permissions required by the CLI tool. All permission items must be unique strings. The system verifies whether the caller has the required permissions when executing the tool. If the caller does not have the required permissions, the tool cannot be executed. Default value is an empty array. |
| inputSchema        | Record<string, Object>     | Yes   | No   | Input schema definition of the CLI tool. It uses the JSON Schema format to define the structure and type of input parameters, and is used to describe the input data format accepted by the tool. |
| outputSchema       | Record<string, Object>     | Yes   | No   | Output schema definition of the CLI tool. It uses the JSON Schema format to define the structure and type of output data, and is used to describe the output data format returned by the tool. |
| eventTypes         | Array\<string>                                         | Yes   | Yes   | List of custom event types supported by the CLI tool. All event types must be unique strings. Default value is an empty array. |
| eventSchemas       | Record<string, Record<string, Object>> | Yes   | Yes   | Schema definition of custom events. Stored in key-value pairs, where the key is the event type and the value is the JSON Schema definition of the event. Default value is an empty object. |
| hasSubCommand      | boolean                                                | Yes   | Yes   | Indicates whether the tool supports subcommands. The value true indicates that the tool supports subcommands, and false indicates that it does not. Default value is false. |
| subcommands        | Record<string, [SubCommandInfo](#subcommandinfo)>       | Yes   | Yes   | List of subcommand information. Stored in key-value pairs, where the key is the subcommand name and the value is the detailed information of the subcommand. Default value is an empty object. |
| isLockScreenExecutionAllowed        | boolean       | Yes   | Yes   | Indicates whether the tool supports execution in the lock screen state. The value true indicates that the tool supports execution in the lock screen state, and false indicates that it does not. Default value is false. |

## ToolSummary

Describes the summary information of a CLI tool.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

| Name        | Type   | Read-only | Optional | Description                                                  |
| ----------- | ------ | --------- | -------- | ------------------------------------------------------------ |
| name        | string | Yes       | No       | Name of the CLI tool.                                        |
| version     | string | Yes       | No       | Version number of the CLI tool. It follows the semantic versioning specification (for example, "1.0.0"), and the format is defined by the provider. |
| description | string | Yes       | No       | Description of the CLI tool.                                 |

## SubCommandInfo

Describes the information about a CLI tool subcommand.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

| Name               | Type                                                   | Read-only | Optional | Description                                                  |
| ------------------ | ------------------------------------------------------ | --------- | -------- | ------------------------------------------------------------ |
| description        | string                                                 | Yes       | No       | Description of the subcommand. It should clearly describe the specific function and usage scenario of the subcommand. |
| requirePermissions | Array\<string>                                      | Yes       | Yes      | List of permissions required by the subcommand. All permission items must be unique strings. The system verifies whether the caller has the required permissions when executing the subcommand. The subcommand cannot be executed without the required permissions. Default value is an empty array. |
| inputSchema        | Record<string, Object>                                 | Yes       | No       | Input schema definition of the subcommand. Defines the structure and type of the input parameters in JSON Schema format. |
| outputSchema       | Record<string, Object>                                 | Yes       | No       | Output schema definition of the subcommand. Defines the structure and type of the output data in JSON Schema format. |
| eventTypes         | Array\<string>                                      | Yes       | Yes      | List of custom event types supported by the subcommand. All event types must be unique strings. Default value is an empty array. |
| eventSchemas       | Record<string, Record<string, Object>>                 | Yes       | Yes      | Schema definition of the custom events of the subcommand. Stored in key-value pairs, where the key is the event type and the value is the JSON Schema definition of the event. Default value is an empty object. |