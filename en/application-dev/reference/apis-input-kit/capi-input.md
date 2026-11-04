# input

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1a59b01eb09cbde916aad8893b634e85d3707880 translatedAt=2026-11-04T01:00:48.084Z pushedAt=2026-11-04T03:24:28.426Z nl=1 -->

## Overview

Provides C APIs of the multimodal input module, supporting event processing for various input devices such as touch, key, and mouse. It enables unified access to multiple devices, improving development efficiency and application interaction experience.

**Since**: 12
## Files

| **Name**| Description|
| -- | -- |
| [oh_axis_type.h](capi-oh-axis-type-h.md) | Enumerates the axis events of an input device. The axis type defines the physical behavior characteristics of an input device in different interaction scenarios, and the system uses the axis type to distinguish and deliver different gesture interaction information. |
| [oh_input_manager.h](capi-oh-input-manager-h.md) | Provides functions such as input event injection, key state query, device hot-plug listening, event interception, shortcut key management, mouse cursor management, input device information query, and injection permission management. |
| [oh_key_code.h](capi-oh-key-code-h.md) | Defines key codes of the key device.|
| [oh_pointer_style.h](capi-oh-pointer-style-h.md) | Defines the mouse pointer styles.|
