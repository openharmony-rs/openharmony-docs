# Input_AxisEvent

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:19:36.981Z pushedAt=2026-06-12T02:34:12.668Z -->

```c
typedef struct Input_AxisEvent Input_AxisEvent
```

## Overview

Defines an axis event object, which is used to represent axis event data from an input device, such as joystick movement on a gamepad and mouse wheel scrolling. You can obtain axis value changes from the input device through axis events to implement precise input control and enhance user interaction experience.

**Since**: 12

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

**Related APIs**:

| Name| Description|
| -- | -- |
| [OH_Input_CreateAxisEvent](capi-oh-input-manager-h.md#oh_input_createaxisevent) | Creates an axis event object. You can call [OH_Input_DestroyAxisEvent](capi-oh-input-manager-h.md#oh_input_destroyaxisevent) to destroy an axis event object.|
| [OH_Input_DestroyAxisEvent](capi-oh-input-manager-h.md#oh_input_destroyaxisevent) | Destroys an axis event object.|