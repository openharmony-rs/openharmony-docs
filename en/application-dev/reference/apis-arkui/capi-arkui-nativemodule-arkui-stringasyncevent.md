# ArkUI_StringAsyncEvent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=92567145241181b97abe57e944e177355e50f4eb translatedAt=2026-08-21T01:43:07.094Z pushedAt=2026-08-21T02:17:13.158Z -->

```c
typedef struct {...} ArkUI_StringAsyncEvent
```

## Overview

Defines the string type parameter used by the component callback event, which is used to pass string data in the asynchronous event callback of a component. It applies to scenarios where a component callback event needs to carry text information.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* pStr | String data passed in the component callback event. |