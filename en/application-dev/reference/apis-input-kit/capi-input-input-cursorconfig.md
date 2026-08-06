# Input_CursorConfig

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:19:31.623Z pushedAt=2026-06-12T02:34:14.298Z -->

```c
typedef struct Input_CursorConfig Input_CursorConfig
```

## Overview

Defines custom mouse cursor configuration, which is used to define and manage the display style and interaction behavior of the mouse cursor in an application. It supports different cursor styles (such as default, hand, and text input), providing users with more intuitive operation feedback and enhancing user experience.

**Since**: 22

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

**Related APIs**:

| Name| Description|
| -- | -- |
| [OH_Input_CursorConfig_Create](capi-oh-input-manager-h.md#oh_input_cursorconfig_create) | Creates a custom mouse cursor configuration object. You can call [OH_Input_CursorConfig_Destroy](capi-oh-input-manager-h.md#oh_input_cursorconfig_destroy) to destroy a custom mouse cursor configuration object.|
| [OH_Input_CursorConfig_Destroy](capi-oh-input-manager-h.md#oh_input_cursorconfig_destroy) | Destroys a custom mouse cursor configuration object.|