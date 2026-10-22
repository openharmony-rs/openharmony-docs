# Input_KeyState

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=527ac908d69187319557716a0a0cfad380663b5d translatedAt=2026-09-11T00:09:43.403Z pushedAt=2026-09-11T02:45:44.196Z -->

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
| [OH_Input_CreateKeyState](capi-oh-input-manager-h.md#oh_input_createkeystate) | Creates a key state structure object. The structure object can be destroyed via [OH_Input_DestroyKeyState](capi-oh-input-manager-h.md#oh_input_destroykeystate). |
| [OH_Input_DestroyKeyState](capi-oh-input-manager-h.md#oh_input_destroykeystate) | Destroys a key state structure object. |
