# ArkUI_TextChangeEvent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=89682c631d1be2b78acdb9477c9eda01133e0baf translatedAt=2026-08-21T01:43:43.238Z pushedAt=2026-08-21T02:27:09.009Z -->

```c
typedef struct {...} ArkUI_TextChangeEvent
```

## Overview

Defines a text change event, which is used to listen for and handle text changes in text input scenarios. This struct contains the text content, extended information, and numeric parameters, allowing you to obtain text change data in real time. It applies to scenarios such as input box content monitoring, real-time search, and character count.

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