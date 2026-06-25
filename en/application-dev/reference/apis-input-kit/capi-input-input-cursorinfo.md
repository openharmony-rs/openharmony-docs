# Input_CursorInfo

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:19:46.294Z pushedAt=2026-06-12T02:34:16.074Z -->

```c
typedef struct Input_CursorInfo Input_CursorInfo
```

## Overview

Defines mouse cursor information. It is used to manage and control the display behavior and appearance properties of the mouse cursor in the input system, including cursor display state, cursor style, cursor size level, and cursor color.

**Since**: 22

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

**Related APIs**:

| Name| Description|
| -- | -- |
| [OH_Input_CursorInfo_Create](capi-oh-input-manager-h.md#oh_input_cursorinfo_create) | Creates a mouse cursor information object. You can call [OH_Input_CursorInfo_Destroy](capi-oh-input-manager-h.md#oh_input_cursorinfo_destroy) to destroy a mouse cursor information object.|
| [OH_Input_CursorInfo_Destroy](capi-oh-input-manager-h.md#oh_input_cursorinfo_destroy) | Destroys the mouse cursor information object.|