# NativeChildProcess_FdList

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b64fba1a3bfa56ac6a22a458a141c3f45d9c160b translatedAt=2026-09-03T09:01:10.483Z pushedAt=2026-09-05T10:47:30.132Z -->

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
