# ArkUI_StringAsyncEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8aba8af2dd3078d46b6b1b6a52500398dc05aaf4 translatedAt=2026-09-22T09:08:13.345Z pushedAt=2026-09-22T10:50:51.453Z -->

```c
typedef struct {...} ArkUI_StringAsyncEvent
```

## Overview

Defines the type of string parameters used in component callback events. This struct is used to pass string data in the asynchronous event callback of a component. It is applicable to scenarios where the component callback event needs to carry text information.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* pStr | Pointer to the string data passed in the component callback event. |


