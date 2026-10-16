# input

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=6ff193a1258b05452b4935e34a160adf6db64d7a translatedAt=2026-09-11T00:10:31.511Z pushedAt=2026-09-11T02:38:58.991Z -->

## Overview

Provides C APIs of the multimodal input module, supporting event processing for various input devices such as touch, key, and mouse. It enables unified access to multiple devices, improving development efficiency and application interaction experience.

**Since**: 12
## Files

| **Name**| Description|
| -- | -- |
| [oh_axis_type.h](capi-oh-axis-type-h.md) | Enumerates the axis events of input devices. An axis type defines the physical behavior characteristics of an input device in different interaction scenarios, and the system distinguishes and delivers different gesture interaction information based on the axis type. |
| [oh_input_manager.h](capi-oh-input-manager-h.md) | Provides functions for input event injection, key state query, device hot swapping monitoring, event interception, shortcut key management, mouse cursor management, input device information query, and injection permission management. |
| [oh_key_code.h](capi-oh-key-code-h.md) | Defines key codes of the key device.|
| [oh_pointer_style.h](capi-oh-pointer-style-h.md) | Defines the mouse pointer styles.|
