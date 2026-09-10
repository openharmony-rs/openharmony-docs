# input

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=a42f8feedc5dcea22b2974f472d01ab7526f02c7 translatedAt=2026-09-01T01:18:19.395Z pushedAt=2026-09-03T06:18:30.559Z -->

## Overview

Provides C APIs of the multimodal input module, supporting event processing for various input devices such as touch, key, and mouse. It enables unified access to multiple devices, improving development efficiency and application interaction experience.

**Since**: 12

## Files

| **Name**| Description|
| -- | -- |
| [oh_axis_type.h](capi-oh-axis-type-h.md) | Defines structure and enumerations for axis events of input devices. Axis types define the physical behavior characteristics of input devices in different interaction scenarios. The system uses axis types to distinguish and convey different gesture interaction information. |
| [oh_input_manager.h](capi-oh-input-manager-h.md) | Provides functions for input event injection, key state query, device hot swapping monitoring, event interception, shortcut key management, mouse cursor management, input device information query, and injection permission management. |
| [oh_key_code.h](capi-oh-key-code-h.md) | Defines key codes of the key device.|
| [oh_pointer_style.h](capi-oh-pointer-style-h.md) | Defines the mouse pointer styles.|