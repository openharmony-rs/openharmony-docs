# @ohos.app.cli.cliManager(CLI Tool Management)

This module provides the capability to interact with system command-line interface (CLI) tools, including querying tool information, invoking and executing CLI commands, and managing sessions. A session is created when the execTool API is called, and is used to track the execution status and result of the CLI tool.

@namespace cliManager

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace cliManager--><!--Device-unnamed-declare namespace cliManager-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [clearSession](arkts-ability-climanager-clearsession-f.md) | Closes a session and forcibly terminates the associated command process. |
| [execCmd](arkts-ability-climanager-execcmd-f.md) | Executes a raw command string in the system shell environment. |
| [querySession](arkts-ability-climanager-querysession-f.md) | Queries the current status and execution result of a session. |
| [sendMessage](arkts-ability-climanager-sendmessage-f.md) | Sends a message to the standard input of a running command process. |
| [subscribeSession](arkts-ability-climanager-subscribesession-f.md) | Subscribes to events from a CLI tool or command execution session. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [execTool](arkts-ability-climanager-exectool-f-sys.md) | Execute a CLI command |
| [getToolInfoByName](arkts-ability-climanager-gettoolinfobyname-f-sys.md) | Get detailed information of a single tool by its name |
| [queryTools](arkts-ability-climanager-querytools-f-sys.md) | Query all detailed information of tools |
| [queryToolSummaries](arkts-ability-climanager-querytoolsummaries-f-sys.md) | Query all tool summary information. The summary information only contains the fields: name, description, version. |
| [registerCliHook](arkts-ability-climanager-registerclihook-f-sys.md) | Register a CLI hook for intercepting tool and command execution. Only one CLI hook can be registered at a time; registering again while one is already active will fail. This API is only available in developer mode. To update a registered hook, call unregisterCliHook first, then register again. The hook object must implement at least one of the optional methods in CliHook. |
| [unregisterCliHook](arkts-ability-climanager-unregisterclihook-f-sys.md) | Unregister the previously registered CLI hook. The hook object must be the same as the one passed to registerCliHook. If no hook is registered, the call will fail with an error. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CliSessionInfo](arkts-ability-climanager-clisessioninfo-i.md) | Describes the session information of a CLI tool or command execution. |
| [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i.md) | Describes the options for executing a raw command string via [execCmd](arkts-ability-climanager-execcmd-f.md). |
| [ExecResult](arkts-ability-climanager-execresult-i.md) | Describes the execution result of a tool or command. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i-sys.md) | Describes the options for executing a raw command string via [execCmd](arkts-ability-climanager-execcmd-f.md). |
| [ExecOptions](arkts-ability-climanager-execoptions-i-sys.md) | Tool execution options. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [SessionStatus](arkts-ability-climanager-sessionstatus-e.md) | Enumerates the status values of a CLI tool or commad execution session. |
