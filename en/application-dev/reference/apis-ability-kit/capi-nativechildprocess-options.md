# NativeChildProcess_Options

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=39c91f6014aebaf032e76cba1dba0db7318cd7f0 translatedAt=2026-09-03T09:02:55.079Z pushedAt=2026-09-05T10:47:30.137Z -->

```c
typedef struct {...} NativeChildProcess_Options
```

## Overview

The struct describes the options used for starting a child process.

**Since**: 13

**Related module**: [ChildProcess](capi-childprocess.md)

**Header file**: [native_child_process.h](capi-native-child-process-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [NativeChildProcess_IsolationMode](capi-native-child-process-h.md#nativechildprocess_isolationmode) isolationMode | Isolation mode of the child process.|
| int64_t reserved | Reserved for future use.|
