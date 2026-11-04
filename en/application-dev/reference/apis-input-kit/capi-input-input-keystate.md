# Input_KeyState

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=29ec5e2798cba0f61c9ee386abf0db610c29644e translatedAt=2026-11-04T00:59:57.403Z pushedAt=2026-11-04T03:24:28.420Z nl=1 -->

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
| [OH_Input_CreateKeyState](capi-oh-input-manager-h.md#oh_input_createkeystate) | Creates a key state struct object. Destroys the key state struct object by calling [OH_Input_DestroyKeyState](capi-oh-input-manager-h.md#oh_input_destroykeystate). |
| [OH_Input_DestroyKeyState](capi-oh-input-manager-h.md#oh_input_destroykeystate) | Destroys a key state struct object. |
