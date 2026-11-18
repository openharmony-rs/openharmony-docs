# @ohos.app.cli.cliManager (CLI Tool Management)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=42e9b25a9eab986eb1a451cdabe085b889bf8e44 translatedAt=2026-11-03T13:25:05.322Z pushedAt=2026-11-04T03:34:51.714Z nl=1 -->

This module provides the capability for third-party applications to interact with system command-line tools (CLI). It can execute shell commands and manage sessions. A session is created when the execCmd API is called, and is used to track the execution status and results of a command.

**Since:** 26.0.1

## Modules to Import

```ts
import { cliManager } from '@kit.AbilityKit';
```

## ExecCmdOptions

Optional parameters for executing a shell command. They can be used to specify the working directory, environment variables, whether to run in the background, foreground execution duration, timeout duration, security policy, and event callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

| Name       | Type | Read-only | Optional | Description |
| ---------- | ---- | ---- | ---- | ------------------ |
| workDir    | string | No | Yes | Working directory for command execution. If this parameter is not passed or is empty, the root directory is used. |
| env        | Record\<string, string\> | No | Yes | Environment variables for command execution. |
| background | boolean | No | Yes | Whether the command is executed in the background.<br/>true: background execution; false: foreground execution.<br/>Default value: false. |
| yieldMs    | number | No | Yes | Foreground execution duration of the command, in milliseconds. Value range: 0 to 1000 * timeout. Default value: 0. If the value is out of range, error code 401 is thrown. |
| timeout    | number | No | Yes | Timeout duration for command execution, in seconds. Value range: 0 to 1800. Default value: 1800. Passing 0 means no timeout. If the value is out of range, error code 401 is thrown. |
| policy     | string | No | Yes | Security policy. The parameter is in JSON string format. |
| callback   | [ToolEventCallback](js-apis-inner-application-toolEventCallback.md) | No | Yes | Event callback used to receive tool events. If this parameter is provided, session events are automatically subscribed. |

## ExecResult

Represents the result of CLI tool execution, including the exit code, standard output, standard error output, termination signal, timeout status, and execution duration of the CLI tool.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

| Name          | Type     | Read-only | Optional | Description |
| ------------- | ------- | ---- | ---  |----------------- |
| exitCode      | number  | No   | Yes   | Exit code of the tool. Default value: undefined. |
| outputText    | string  | No   | Yes   | Standard output (stdout) of the tool. Default value: undefined. |
| errorText     | string  | No   | Yes   | Standard error output (stderr) of the tool. Default value: undefined. |
| signalNumber  | number  | No   | Yes   | Termination signal of the tool. Default value: undefined. |
| timeOut       | boolean | No   | No   | Whether the execution of the tool timed out. true indicates a timeout, and false indicates no timeout. Default value: false. |
| executionTime | number  | No   | No   | Execution duration of the tool. Unit: ms. Default value: 0. |

## SessionStatus

When a CLI tool is executed, the system creates a session between the caller and the CLI tool. This field describes the session status.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

| Name      | Value   | Description                   |
| --------- | ---- | ---------------------- |
| RUNNING   | 'running' | The session is in progress.    |
| COMPLETED   | 'completed' | The session is completed.    |
| FAILED    | 'failed' | The session has failed.    |

## CliSessionInfo

When a CLI tool is executed, the system creates a session between the caller and the CLI tool. This field describes the format of the session information.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

| Name      | Type | Read-only | Optional | Description |
| --------- | ---- | ---- | --- | ------------------ |
| sessionId  | string | No | No | Session ID. |
| toolName  | string | No | No | Tool name. |
| status  | [SessionStatus](#sessionstatus) | No | No | Session status. |
| result  | [ExecResult](#execresult) | No | Yes | Tool execution result. Default value: undefined. |

## cliManager.execCmd

execCmd(cmd: string, execCmdOptions?: ExecCmdOptions): Promise\<CliSessionInfo\>

Executes a shell command and returns the session information. This API uses a promise to return the result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required Permission**: ohos.permission.EXEC_CLI_TOOL (configurable only for system applications) or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| cmd | string | Yes | Shell command to execute. |
| execCmdOptions | [ExecCmdOptions](#execcmdoptions) | No | Optional parameters for executing the command. Default value: see the default values of the specific attributes in [ExecCmdOptions](#execcmdoptions). |

**Returns**

| Type | Description |
| -------- | -------- |
| Promise\<[CliSessionInfo](#clisessioninfo)\> | Promise object. Returns the session information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 801 | Capability not supported. Possible causes: Failed to call the API due to limited device capabilities. |
| 35600031 | Maximum number of processes has been reached. |
| 35600050  | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |

**Example**

```ts
import { cliManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let cmd: string = 'ls -l';
  let options: cliManager.ExecCmdOptions = {
    background: false,
    timeout: 60,
    workDir: '/system/bin',
    callback: {
      onEvent: (event) => {
        hilog.info(0x0000, 'CliManager', 'event type: %{public}s, data: %{public}s', event.toolEventType, event.data);
      }
    }
  };
  cliManager.execCmd(cmd, options).then((sessionInfo) => {
    hilog.info(0x0000, 'CliManager', 'execCmd success, sessionId: %{public}s, status: %{public}s',
      sessionInfo.sessionId, sessionInfo.status);
  }).catch((error: BusinessError) => {
    hilog.error(0x0000, 'CliManager', 'execCmd failed, code: %{public}d, message: %{public}s', error.code, error.message);
  });
} catch (error) {
  hilog.error(0x0000, 'CliManager', 'execCmd failed, error: %{public}s', JSON.stringify(error));
}
```

## cliManager.subscribeSession

subscribeSession(sessionId: string, callback: ToolEventCallback): Promise\<void\>

Subscribes to the events of a specified CLI tool session. During the session, the standard output, standard error, exit, or error events generated by the CLI tool are returned through the callback.

> **NOTE**
>
> - The session is limited to the creating process for management: only the process that calls `execCmd` to create the session can call this API. Even if other processes obtain the `sessionId`, calling this API throws error code 201 (Permission denied).
> - If an event callback has already been provided through the callback parameter of [ExecCmdOptions](#execcmdoptions) when calling [execCmd](#climanagerexeccmd), there is no need to call this API again.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required Permission**: ohos.permission.EXEC_CLI_TOOL (configurable for system applications) or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters**

| Name | Type                                      | Mandatory | Description                         |
| -------------- | ----------------------------------------- | --------- | ----------------------------------- |
| sessionId      | string                                    | Yes       | Session ID of the target CLI tool process. |
| callback       | [ToolEventCallback](js-apis-inner-application-toolEventCallback.md) | Yes       | Callback for the CLI tool session event. |

**Returns**

| Type           | Description                                 |
| -------------- | ------------------------------------------- |
| Promise\<void\> | Promise that returns no value.       |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 35600032 | The specified session does not exist.                                  |
| 35600050 | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |

**Example**

```ts
import { cliManager, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let sessionId = 'example_session_id';
// Define the CLI tool session event callback.
let callback: common.ToolEventCallback = {
  onEvent: (event: common.CliToolEvent) => {
    hilog.info(0x0000, 'CliManager', 'subscribeSession event type: %{public}s, data: %{public}s',
      event.toolEventType, event.data);
  }
};

try {
  // Subscribe to events of the specified session.
  cliManager.subscribeSession(sessionId, callback).then(() => {
    hilog.info(0x0000, 'CliManager', 'subscribeSession success.');
  }).catch((error: BusinessError) => {
    hilog.error(0x0000, 'CliManager', 'subscribeSession failed, code: %{public}d, message: %{public}s',
      error.code, error.message);
  });
} catch (error) {
  hilog.error(0x0000, 'CliManager', 'subscribeSession failed, error: %{public}s', JSON.stringify(error));
}
```

## cliManager.clearSession

clearSession(sessionId: string): Promise\<void\>

Closes the specified CLI tool session and forcibly terminates the corresponding tool process.

> **NOTE**
>
> - The session is limited to the creating process: only the process that calls `execCmd` to create the session can call this API. Even if other processes obtain the `sessionId`, calling this API throws error code 201 (Permission denied).

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required Permission**: ohos.permission.EXEC_CLI_TOOL (configurable for system applications) or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters**

| Name | Type   | Mandatory | Description                              |
| -------------- | ------ | --------- | ---------------------------------------- |
| sessionId      | string | Yes       | Session ID of the target CLI tool process. |

**Returns**

| Type           | Description                              |
| -------------- | ---------------------------------------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 35600032 | The specified session does not exist.                                  |
| 35600050 | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |

**Example**

```ts
import { cliManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let sessionId = 'example_session_id';
try {
  // Clear the specified session
  cliManager.clearSession(sessionId).then(() => {
    hilog.info(0x0000, 'CliManager', 'clearSession success.');
  }).catch((error: BusinessError) => {
    hilog.error(0x0000, 'CliManager', 'clearSession failed, code: %{public}d, message: %{public}s',
      error.code, error.message);
  });
} catch (error) {
  hilog.error(0x0000, 'CliManager', 'clearSession failed, error: %{public}s', JSON.stringify(error));
}
```

## cliManager.querySession

querySession(sessionId: string): Promise\<CliSessionInfo\>

Queries the status and execution result of a specified CLI tool session.

> **NOTE**
>
> - The session is limited to the creating process: only the process that calls `execCmd` to create the session can call this API. Even if other processes obtain the `sessionId`, calling this API throws error code 201 (Permission denied).

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required Permission**: ohos.permission.EXEC_CLI_TOOL (configurable only for system applications) or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters**

| Name | Type   | Mandatory | Description                          |
| -------------- | ------ | --------- | ------------------------------------ |
| sessionId      | string | Yes       | Session ID of the target CLI tool process. |

**Returns**

| Type                                      | Description                               |
| ----------------------------------------- | ----------------------------------------- |
| Promise\<[CliSessionInfo](#clisessioninfo)\> | Promise used to return the CLI tool session information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 35600032 | The specified session does not exist.                                  |
| 35600050 | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |

**Example**

```ts
import { cliManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let sessionId = 'example_session_id';
try {
  // Query the status and execution result of the specified session.
  cliManager.querySession(sessionId).then((sessionInfo) => {
    hilog.info(0x0000, 'CliManager', 'querySession success, status: %{public}s', sessionInfo.status);
  }).catch((error: BusinessError) => {
    hilog.error(0x0000, 'CliManager', 'querySession failed, code: %{public}d, message: %{public}s',
      error.code, error.message);
  });
} catch (error) {
  hilog.error(0x0000, 'CliManager', 'querySession failed, error: %{public}s', JSON.stringify(error));
}
```

## cliManager.sendMessage

sendMessage(sessionId: string, message: string): Promise\<void\>

Sends a message to the process corresponding to the specified CLI tool session.

> **NOTE**
>
> - The session is limited to the creating process: only the process that calls `execCmd` to create the session can call this API. Even if other processes obtain the `sessionId`, calling this API throws error code 201 (Permission denied).

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required Permission**: ohos.permission.EXEC_CLI_TOOL (configurable for system applications) or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters**

| Name | Type   | Mandatory | Description                                  |
| -------------- | ------ | --------- | -------------------------------------------- |
| sessionId      | string | Yes       | Session ID of the target CLI tool process.   |
| message        | string | Yes       | Message to send. The maximum length is 10240 characters. Error code 401 is thrown when the maximum length is exceeded. |

**Returns**

| Type           | Description                     |
| -------------- | ------------------------------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 35600032 | The specified session does not exist.                                  |
| 35600033 | Failed to write message to the tool process.                             |
| 35600050 | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |

**Example**

```ts
import { cliManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let sessionId = 'example_session_id';
let message = 'example message';
try {
  // Send a message to the specified session.
  cliManager.sendMessage(sessionId, message).then(() => {
    hilog.info(0x0000, 'CliManager', 'sendMessage success.');
  }).catch((error: BusinessError) => {
    hilog.error(0x0000, 'CliManager', 'sendMessage failed, code: %{public}d, message: %{public}s',
      error.code, error.message);
  });
} catch (error) {
  hilog.error(0x0000, 'CliManager', 'sendMessage failed, error: %{public}s', JSON.stringify(error));
}
```
