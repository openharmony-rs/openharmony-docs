# Input_CursorInfo

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1a59b01eb09cbde916aad8893b634e85d3707880 translatedAt=2026-11-04T04:29:30.542Z pushedAt=2026-11-04T08:04:44.662Z nl=1 -->

```c
typedef struct Input_CursorInfo Input_CursorInfo
```

## Overview

Defines the mouse cursor information, which is used to describe the display behavior and appearance attributes of the mouse cursor in the input system, including the cursor display state, cursor style, cursor size level, and cursor color.

**Since**: 22

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

**Related APIs**:

| Name| Description|
| -- | -- |
| [OH_Input_CursorInfo_Create](capi-oh-input-manager-h.md#oh_input_cursorinfo_create) | Creates a mouse cursor information object. You can call [OH_Input_CursorInfo_Destroy](capi-oh-input-manager-h.md#oh_input_cursorinfo_destroy) to destroy a mouse cursor information object.|
| [OH_Input_CursorInfo_Destroy](capi-oh-input-manager-h.md#oh_input_cursorinfo_destroy) | Destroys the mouse cursor information object.|
