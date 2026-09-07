# Input_KeyState

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=0ef6d7cd8e5d921a68eb0a763cb21bfc9319a3b1 translatedAt=2026-09-01T01:18:18.853Z pushedAt=2026-09-03T06:15:11.854Z -->

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
| [OH_Input_CreateKeyState](capi-oh-input-manager-h.md#oh_input_createkeystate) | Creates a key state struct object. The struct object can be destroyed via [OH_Input_DestroyKeyState](capi-oh-input-manager-h.md#oh_input_destroykeystate). |
| [OH_Input_DestroyKeyState](capi-oh-input-manager-h.md#oh_input_destroykeystate) | Destroys a key status enum object.|