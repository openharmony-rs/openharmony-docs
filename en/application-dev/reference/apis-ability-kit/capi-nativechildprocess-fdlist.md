# NativeChildProcess_FdList

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b33c416f2dabc1fc4149b71a7ef553e301b3c3cc translatedAt=2026-10-09T10:38:50.289Z pushedAt=2026-10-10T01:48:49.221Z -->

```c
typedef struct NativeChildProcess_FdList {...} NativeChildProcess_FdList
```

## Overview

Defines the list of file descriptor information passed to the child process. The number of file descriptor records must not exceed 16; exceeding the limit will cause the child process creation to fail.

**Since**: 13

**Related module**: [ChildProcess](capi-childprocess.md)

**Header file**: [native_child_process.h](capi-native-child-process-h.md)

## Summary

### Member Variables

| Name                                    | Description|
|----------------------------------------| -- |
| struct [NativeChildProcess_Fd](capi-nativechildprocess-fd.md)* head | Pointer to the first record in the linked list of child process file descriptor records. |
