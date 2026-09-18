# @ohos.app.cli.cliManager

The module provides the capability to interact with cli tools in the system.

@namespace cliManager

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cliManager } from '@kit.AbilityKit';
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
| [sendMessage](arkts-ability-climanager-sendmessage-f-sys.md) | Send event to target process. |
| [subscribeSession](arkts-ability-climanager-subscribesession-f-sys.md) | Subscribe session event. |
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
