# NativeChildProcess_Args

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=5190a496e705e7a7abad7605c46f720b1c829b58 translatedAt=2026-09-03T09:00:04.732Z pushedAt=2026-09-05T10:47:30.126Z -->

```c
typedef struct {...} NativeChildProcess_Args
```

## Overview

The struct describes the parameters passed to the child process.

**Since**: 13

**Related module**: [ChildProcess](capi-childprocess.md)

**Header file**: [native_child_process.h](capi-native-child-process-h.md)

## Summary

### Member Variables

| Name                                         | Description|
|---------------------------------------------| -- |
| char* entryParams                           | String of parameters passed to the entry function of the child process. entryParams is transmitted over IPC, and the maximum amount of data transmitted over IPC is 200 KB (for details, see [Constraints](../../ipc/ipc-rpc-overview.md#constraints)). Part of this amount is occupied by the system. It is recommended that the amount of data passed in entryParams not exceed 150 KB; otherwise, the child process may fail to be created. |
| struct [NativeChildProcess_FdList](capi-nativechildprocess-fdlist.md) fdList | List of file descriptor information passed to the child process. The number of file descriptor records cannot exceed 16. The child process can communicate with the main process through these file descriptors. |
