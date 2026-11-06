# Input_Hotkey

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:19:58.840Z pushedAt=2026-06-12T02:42:36.721Z -->

```c
typedef struct Input_Hotkey Input_Hotkey
```

## Overview

Defines the hotkey struct, which describes the hotkey design logic such as the key combination, trigger conditions, and callback handling. Applications can register and manage custom hotkeys.

**Since**: 14

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

**Related APIs**:

| Name| Description|
| -- | -- |
| [OH_Input_CreateHotkey](capi-oh-input-manager-h.md#oh_input_createhotkey) | Creates a hotkey object. You can call [OH_Input_DestroyHotkey](capi-oh-input-manager-h.md#oh_input_destroyhotkey) to destroy a hotkey object.|
| [OH_Input_DestroyHotkey](capi-oh-input-manager-h.md#oh_input_destroyhotkey) | Destroys a hotkey object.|