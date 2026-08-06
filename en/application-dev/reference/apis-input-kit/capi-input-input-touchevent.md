# Input_TouchEvent

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:20:33.627Z pushedAt=2026-06-12T03:09:21.650Z -->

```c
typedef struct Input_TouchEvent Input_TouchEvent
```

## Overview

Defines the touchscreen input event object, which is used to represent detailed information about touchscreen input, including the touch point position, touch state, and timestamp.

**Since**: 12

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

**Related APIs**:

| Name| Description|
| -- | -- |
| [OH_Input_CreateTouchEvent](capi-oh-input-manager-h.md#oh_input_createtouchevent) | Creates a touch event object. You can call [OH_Input_DestroyTouchEvent](capi-oh-input-manager-h.md#oh_input_destroytouchevent) to destroy a touch event object.|
| [OH_Input_DestroyTouchEvent](capi-oh-input-manager-h.md#oh_input_destroytouchevent) | Destroys a touch event object.|