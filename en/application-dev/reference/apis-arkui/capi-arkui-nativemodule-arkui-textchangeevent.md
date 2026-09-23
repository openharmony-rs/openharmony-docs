# ArkUI_TextChangeEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e96737317627f12dc773a6945dd07b0ba27f19f5 translatedAt=2026-09-22T09:10:11.749Z pushedAt=2026-09-22T10:56:52.122Z -->

```c
typedef struct {...} ArkUI_TextChangeEvent
```

## Overview

Defines a text change event, which is used to listen to and handle text change events in text input scenarios. This struct contains the text content, extended information, and numeric parameters. It allows you to obtain text change data in real time, making it suitable for scenarios such as listening to text box content, real-time search, and word count.

**Since**: 15

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* pStr | Pointer to the text content string in the text change event. |
| const char* pExtendStr | Pointer to the extended string in the text change event, used to store additional text information. |
| int32_t number | Numeric parameter value of the event, used to record the numeric information in the text change event. The value range is [-2147483648, 2147483647]. |


