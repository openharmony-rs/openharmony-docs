# @ohos.process(Process Management)

The **process** module provides process management APIs, for example, APIs for obtaining process information.

**Since:** 7

<!--Device-unnamed-declare namespace process--><!--Device-unnamed-declare namespace process-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [abort](arkts-arkts-process-abort-f.md#abort-1) | Aborts a process and generates a core file. This method will cause a process to exit immediately. Exercise caution when using this method. |
| [getPastCpuTime](arkts-arkts-process-getpastcputime-f.md#getpastcputime-1) | Obtains the CPU time (in milliseconds) from the time the process starts to the current time. |
| [getStartRealtime](arkts-arkts-process-getstartrealtime-f.md#getstartrealtime-1) | Obtains the duration (excluding the system sleep time), in milliseconds, from the time the system starts to the time the process starts. |
| [is64Bit](arkts-arkts-process-is64bit-f.md#is64bit-1) | Checks whether this process is running in a 64-bit environment. |
| [isIsolatedProcess](arkts-arkts-process-isisolatedprocess-f.md#isisolatedprocess-1) | Checks whether this process is isolated. |
| [uptime](arkts-arkts-process-uptime-f.md#uptime-1) | Obtains the running time of the current system, in seconds. |
| [exit](arkts-arkts-process-exit-f.md#exit-1) | Terminates this process. |
| [getEnvironmentVar](arkts-arkts-process-getenvironmentvar-f.md#getenvironmentvar-1) | Obtains the value of an environment variable. |
| [getSystemConfig](arkts-arkts-process-getsystemconfig-f.md#getsystemconfig-1) | Obtains the system configuration. |
| [getThreadPriority](arkts-arkts-process-getthreadpriority-f.md#getthreadpriority-1) | Obtains the thread priority based on the specified TID. |
| [getUidForName](arkts-arkts-process-getuidforname-f.md#getuidforname-1) | Obtains the UID of a user from the user database of the system based on the specified user name. |
| [isAppUid](arkts-arkts-process-isappuid-f.md#isappuid-1) | Checks whether a UID belongs to this application. |
| [kill](arkts-arkts-process-kill-f.md#kill-1) | Sends a signal to a specified process to terminate it. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [chdir](arkts-arkts-process-chdir-f-sys.md#chdir-1) | Change current directory |
| [cwd](arkts-arkts-process-cwd-f-sys.md#cwd-1) | Return the current work directory; |
| [off](arkts-arkts-process-off-f-sys.md) | Remove registered event |
| [on](arkts-arkts-process-on-f-sys.md) | Register for an event |
| [runCmd](arkts-arkts-process-runcmd-f-sys.md#runcmd-1) | Returns a child process object and spawns a new ChildProcess to run the command. |
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
