# Input_KeyState

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:20:17.893Z pushedAt=2026-06-12T03:03:28.841Z -->

```c
typedef struct Input_KeyState Input_KeyState
```

## **Overview**

Defines key information used to identify key behavior. For example, the "Ctrl" key information includes the key value and key state. It is applicable to scenarios such as hotkey processing, input event state management, and key state detection.

**Since**: 12

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

**Related APIs**:

| Name| Description|
| -- | -- |
| [OH_Input_CreateKeyState](capi-oh-input-manager-h.md#oh_input_createkeystate) | Creates a key status enum object. You can call [OH_Input_DestroyKeyState](capi-oh-input-manager-h.md#oh_input_destroykeystate) to destroy a key status enum object.|
| [OH_Input_DestroyKeyState](capi-oh-input-manager-h.md#oh_input_destroykeystate) | Destroys a key status enum object.|