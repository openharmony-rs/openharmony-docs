# oh_pointer_style.h

## Overview

**Include**: <multimodalinput/oh_pointer_style.h>

**Library**: libohinput.so

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Related module**: [input](capi-input.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Input_PointerStyle](#input_pointerstyle) | Input_PointerStyle | Enumerates the pointer styles. |

### Macro

| Name | Description |
| -- | -- |
| OH_POINTER_STYLE_H | Defines the mouse pointer styles.<br>**Since**: 22<br>**System capability**: SystemCapability.MultimodalInput.Input.Core |

## Enum type description

### Input_PointerStyle

```c
enum Input_PointerStyle
```

**Description**

Enumerates the pointer styles.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 22

| Enum item | Description |
| -- | -- |
| DEFAULT = 0 | Cursor style displayed when no specific style is set by the application.<br>**Since**: 22 |
| EAST = 1 | East arrow<br>**Since**: 22 |
| WEST = 2 | West arrow<br>**Since**: 22 |
| SOUTH = 3 | South arrow<br>**Since**: 22 |
| NORTH = 4 | North arrow<br>**Since**: 22 |
| WEST_EAST = 5 | West-east arrow<br>**Since**: 22 |
| NORTH_SOUTH = 6 | North-south arrow<br>**Since**: 22 |
| NORTH_EAST = 7 | North-east arrow<br>**Since**: 22 |
| NORTH_WEST = 8 | North-west arrow<br>**Since**: 22 |
| SOUTH_EAST = 9 | South-east arrow<br>**Since**: 22 |
| SOUTH_WEST = 10 | South-west arrow<br>**Since**: 22 |
| NORTH_EAST_SOUTH_WEST = 11 | North-east and south-west adjustment<br>**Since**: 22 |
| NORTH_WEST_SOUTH_EAST = 12 | North-west and south-east adjustment<br>**Since**: 22 |
| CROSS = 13 | Cross (accurate selection)<br>**Since**: 22 |
| CURSOR_COPY = 14 | Copy.<br>**Since**: 22 |
| CURSOR_FORBID = 15 | Forbid<br>**Since**: 22 |
| COLOR_SUCKER = 16 | Color picker<br>**Since**: 22 |
| HAND_GRABBING = 17 | Grabbing hand<br>**Since**: 22 |
| HAND_OPEN = 18 | Opening hand<br>**Since**: 22 |
| HAND_POINTING = 19 | Hand-shaped pointer<br>**Since**: 22 |
| HELP = 20 | Help<br>**Since**: 22 |
| MOVE = 21 | Move<br>**Since**: 22 |
| RESIZE_LEFT_RIGHT = 22 | Left and right resizing<br>**Since**: 22 |
| RESIZE_UP_DOWN = 23 | Up and down resizing<br>**Since**: 22 |
| SCREENSHOT_CHOOSE = 24 | Screenshot crosshair<br>**Since**: 22 |
| SCREENSHOT_CURSOR = 25 | Screenshot<br>**Since**: 22 |
| TEXT_CURSOR = 26 | Text selection<br>**Since**: 22 |
| ZOOM_IN = 27 | Zoom in<br>**Since**: 22 |
| ZOOM_OUT = 28 | Zoom out<br>**Since**: 22 |
| MIDDLE_BTN_EAST = 29 | Scrolling east<br>**Since**: 22 |
| MIDDLE_BTN_WEST = 30 | Scrolling west<br>**Since**: 22 |
| MIDDLE_BTN_SOUTH = 31 | Scrolling south<br>**Since**: 22 |
| MIDDLE_BTN_NORTH = 32 | Scrolling north<br>**Since**: 22 |
| MIDDLE_BTN_NORTH_SOUTH = 33 | Scrolling north-south<br>**Since**: 22 |
| MIDDLE_BTN_NORTH_EAST = 34 | Scrolling north-east<br>**Since**: 22 |
| MIDDLE_BTN_NORTH_WEST = 35 | Scrolling north-west<br>**Since**: 22 |
| MIDDLE_BTN_SOUTH_EAST = 36 | Scrolling south-east<br>**Since**: 22 |
| MIDDLE_BTN_SOUTH_WEST = 37 | Scrolling south-west<br>**Since**: 22 |
| MIDDLE_BTN_NORTH_SOUTH_WEST_EAST = 38 | Moving as a cone in four directions<br>**Since**: 22 |
| HORIZONTAL_TEXT_CURSOR = 39 | Horizontal text selection<br>**Since**: 22 |
| CURSOR_CROSS = 40 | Cross<br>**Since**: 22 |
| CURSOR_CIRCLE = 41 | Circle<br>**Since**: 22 |
| LOADING = 42 | Loading<br>**Since**: 22 |
| RUNNING = 43 | Running in the background<br>**Since**: 22 |
| MIDDLE_BTN_EAST_WEST = 44 | Scrolling east-west<br>**Since**: 22 |
| RUNNING_LEFT = 45 | Running in the background (extension 1)<br>**Since**: 22 |
| RUNNING_RIGHT = 46 | Running in the background (extension 2)<br>**Since**: 22 |
| AECH_DEVELOPER_DEFINED_ICON = 47 | Custom circular pointer<br>**Since**: 22 |
| SCREENRECORDER_CURSOR = 48 | Screen recording<br>**Since**: 22 |
| LASER_CURSOR = 49 | Floating This pointer can be used only when the stylus enters the air mouse mode and cannot be directly set.<br> In air mouse mode, you can rotate the stylus in the air to control the movement of the virtual pointer on the screen and press the button on the stylus to turn pages up or down. This mode is used PPT presentation and air gesture control.<br>**Since**: 22 |
| LASER_CURSOR_DOT = 50 | Click This pointer can be used only when the stylus enters the air mouse mode and cannot be directly set.<br>In air mouse mode, you can rotate the stylus in the air to control the movement of the virtual pointer on the screen and press the button on the stylus to turn pages up or down. This mode is used PPT presentation and air gesture control.<br>**Since**: 22 |
| LASER_CURSOR_DOT_RED = 51 | Laser pointer This pointer can be used only when the stylus enters the air mouse mode and cannot be directly set. <br>In air mouse mode, you can rotate the stylus in the air to control the movement of the virtual pointer on the screen and press the button on the stylus to turn pages up or down. This mode is used PPT presentation and air gesture control.<br>**Since**: 22 |
| DEVELOPER_DEFINED_ICON = -100 | Custom pointer. You can use the {@link OH_Input_SetCustomCursor} to set a custom pointer, but not the<br>{@link OH_Input_SetPointerStyle}.<br>**Since**: 22 |


