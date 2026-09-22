# @ohos.app.cli.cliManager

This module provides the capability to interact with system command-line interface (CLI) tools, including querying tool information, invoking and executing CLI commands, and managing sessions. A session is created when the execTool API is called, and is used to track the execution status and result of the CLI tool.

@namespace cliManager

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [clearSession](arkts-ability-climanager-clearsession-f-sys.md) | Close session and force kill tool process. |
| [execCmd](arkts-ability-climanager-execcmd-f-sys.md) | Execute a command. This API uses a promise to return the result. |
| [execTool](arkts-ability-climanager-exectool-f-sys.md) | Execute a CLI command |
| [getToolInfoByName](arkts-ability-climanager-gettoolinfobyname-f-sys.md) | Get detailed information of a single tool by its name |
| [querySession](arkts-ability-climanager-querysession-f-sys.md) | Query session status. |
| [queryTools](arkts-ability-climanager-querytools-f-sys.md) | Query all detailed information of tools |
| [queryToolSummaries](arkts-ability-climanager-querytoolsummaries-f-sys.md) | Query all tool summary information. The summary information only contains the fields: name, description, version. |
| [registerCliHook](arkts-ability-climanager-registerclihook-f-sys.md) | Register a CLI hook for intercepting tool and command execution. Only one CLI hook can be registered at a time; registering again while one is already active will fail. This API is only available in developer mode. To update a registered hook, call unregisterCliHook first, then register again. The hook object must implement at least one of the optional methods in CliHook. |
| [sendMessage](arkts-ability-climanager-sendmessage-f-sys.md) | Send event to target process. |
| [subscribeSession](arkts-ability-climanager-subscribesession-f-sys.md) | Subscribe session event. |
| [unregisterCliHook](arkts-ability-climanager-unregisterclihook-f-sys.md) | Unregister the previously registered CLI hook. The hook object must be the same as the one passed to registerCliHook. If no hook is registered, the call will fail with an error. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CliSessionInfo](arkts-ability-climanager-clisessioninfo-i-sys.md) | Session information of a tool execution. |
| [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i-sys.md) | Options for executing a command. |
| [ExecOptions](arkts-ability-climanager-execoptions-i-sys.md) | Tool execution options. |
| [ExecResult](arkts-ability-climanager-execresult-i-sys.md) | Execute result of a tool execution. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [SessionStatus](arkts-ability-climanager-sessionstatus-e-sys.md) | Enum for session status. |
<!--DelEnd-->
