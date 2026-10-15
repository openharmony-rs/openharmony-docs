# ArkUI_TextChangeEvent

```c
typedef struct ArkUI_TextChangeEvent {...} ArkUI_TextChangeEvent
```

## Overview

Defines a text change event, which is used to listen to and handle text change events in text input scenarios. This struct contains the text content, extended information, and numeric parameters. It allows you to obtain text change data in real time, making it suitable for scenarios such as listening to text box content, real-time search, and word count.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* pStr | String data |
| const char* pExtendStr | Extended string data |
| int32_t number | Numeric data |


