# @ohos.process(Process Management)

The **process** module provides process management APIs, for example, APIs for obtaining process information.

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [abort](arkts-arkts-process-abort-f.md) | Aborts a process and generates a core file. This method will cause a process to exit immediately. Exercise caution when using this method. |
| [exit](arkts-arkts-process-exit-f.md) | Terminates this process. |
| [getEnvironmentVar](arkts-arkts-process-getenvironmentvar-f.md) | Obtains the value of an environment variable. |
| [getPastCpuTime](arkts-arkts-process-getpastcputime-f.md) | Obtains the CPU time (in milliseconds) from the time the process starts to the current time. |
| [getStartRealtime](arkts-arkts-process-getstartrealtime-f.md) | Obtains the duration (excluding the system sleep time), in milliseconds, from the time the system starts to the time the process starts. |
| [getSystemConfig](arkts-arkts-process-getsystemconfig-f.md) | Obtains the system configuration. |
| [getThreadPriority](arkts-arkts-process-getthreadpriority-f.md) | Obtains the thread priority based on the specified TID. |
| [getUidForName](arkts-arkts-process-getuidforname-f.md) | Obtains the UID of a user from the user database of the system based on the specified user name. |
| [is64Bit](arkts-arkts-process-is64bit-f.md) | Checks whether this process is running in a 64-bit environment. |
| [isAppUid](arkts-arkts-process-isappuid-f.md) | Checks whether a UID belongs to this application. |
| [isIsolatedProcess](arkts-arkts-process-isisolatedprocess-f.md) | Checks whether this process is isolated. |
| [kill](arkts-arkts-process-kill-f.md) | Sends a signal to a specified process to terminate it. |
| [uptime](arkts-arkts-process-uptime-f.md) | Obtains the running time of the current system, in seconds. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [chdir](arkts-arkts-process-chdir-f-sys.md) | Change current directory |
| [cwd](arkts-arkts-process-cwd-f-sys.md) | Return the current work directory; |
| [off](arkts-arkts-process-off-f-sys.md) | Remove registered event |
| [on](arkts-arkts-process-on-f-sys.md) | Register for an event |
| [runCmd](arkts-arkts-process-runcmd-f-sys.md) | Returns a child process object and spawns a new ChildProcess to run the command. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [ProcessManager](arkts-arkts-process-processmanager-c.md) | Provides APIs for throwing exceptions during the addition of a process. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ChildProcess](arkts-arkts-process-childprocess-i-sys.md) | The childprocess object can be used to create a new process. |
| [ConditionType](arkts-arkts-process-conditiontype-i-sys.md) | Provides the ConditionType type,including timeout, killSignal, maxBuffer. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [EventListener](arkts-arkts-process-eventlistener-t.md) | Event to store. |

### Constants

| Name | Description |
| --- | --- |
| [pid](arkts-arkts-process-con.md#pid) | Process ID (PID) of the process. |
| [tid](arkts-arkts-process-con.md#tid) | Thread ID (TID) of the thread. |
| [uid](arkts-arkts-process-con.md#uid) | User identifier (UID) of the process. |

<!--Del-->
### Constants(System API)

| Name | Description |
| --- | --- |
| [egid](arkts-arkts-process-con-sys.md#egid) | Returns the numeric valid group ID of the process |
| [euid](arkts-arkts-process-con-sys.md#euid) | Return the numeric valid user identity of the process |
| [gid](arkts-arkts-process-con-sys.md#gid) | Returns the numeric group id of the process |
| [groups](arkts-arkts-process-con-sys.md#groups) | Return an array with supplementary group id |
| [ppid](arkts-arkts-process-con-sys.md#ppid) | Return ppid is The pid of the current child process |
<!--DelEnd-->
