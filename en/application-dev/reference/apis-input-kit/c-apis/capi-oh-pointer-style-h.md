# oh_pointer_style.h

## Overview

Defines the mouse cursor styles.

**File to Include**: <multimodalinput/oh_pointer_style.h>

**Library**: libohinput.so

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 22

**Related module**: [input](capi-input-kit-input.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Input_PointerStyle](#input_pointerstyle) | Input_PointerStyle | Enumerates the cursor styles. |

## Enum type description

### Input_PointerStyle

```c
enum Input_PointerStyle
```

**Description**

Enumerates the cursor styles.

<!--Device-enum Input_PointerStyle--><!--Device-enum Input_PointerStyle-End-->

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 22

| Enum item | Description |
| -- | -- |
| DEFAULT = 0 | Cursor style displayed when no style is set by the app.<br>**Since**: 22<br><!--Device-DEFAULT = 0--><!--Device-DEFAULT = 0-End--> |
| EAST = 1 | East arrow<br>**Since**: 22<br><!--Device-EAST = 1--><!--Device-EAST = 1-End--> |
| WEST = 2 | West arrow<br>**Since**: 22<br><!--Device-WEST = 2--><!--Device-WEST = 2-End--> |
| SOUTH = 3 | South arrow<br>**Since**: 22<br><!--Device-SOUTH = 3--><!--Device-SOUTH = 3-End--> |
| NORTH = 4 | North arrow<br>**Since**: 22<br><!--Device-NORTH = 4--><!--Device-NORTH = 4-End--> |
| WEST_EAST = 5 | West-east arrow<br>**Since**: 22<br><!--Device-WEST_EAST = 5--><!--Device-WEST_EAST = 5-End--> |
| NORTH_SOUTH = 6 | North-south arrow<br>**Since**: 22<br><!--Device-NORTH_SOUTH = 6--><!--Device-NORTH_SOUTH = 6-End--> |
| NORTH_EAST = 7 | North-east arrow<br>**Since**: 22<br><!--Device-NORTH_EAST = 7--><!--Device-NORTH_EAST = 7-End--> |
| NORTH_WEST = 8 | North-west arrow<br>**Since**: 22<br><!--Device-NORTH_WEST = 8--><!--Device-NORTH_WEST = 8-End--> |
| SOUTH_EAST = 9 | South-east arrow<br>**Since**: 22<br><!--Device-SOUTH_EAST = 9--><!--Device-SOUTH_EAST = 9-End--> |
| SOUTH_WEST = 10 | South-west arrow<br>**Since**: 22<br><!--Device-SOUTH_WEST = 10--><!--Device-SOUTH_WEST = 10-End--> |
| NORTH_EAST_SOUTH_WEST = 11 | North-east and south-west adjustment<br>**Since**: 22<br><!--Device-NORTH_EAST_SOUTH_WEST = 11--><!--Device-NORTH_EAST_SOUTH_WEST = 11-End--> |
| NORTH_WEST_SOUTH_EAST = 12 | North-west and south-east adjustment<br>**Since**: 22<br><!--Device-NORTH_WEST_SOUTH_EAST = 12--><!--Device-NORTH_WEST_SOUTH_EAST = 12-End--> |
| CROSS = 13 | Cross (accurate selection)<br>**Since**: 22<br><!--Device-CROSS = 13--><!--Device-CROSS = 13-End--> |
| CURSOR_COPY = 14 | Copy.<br>**Since**: 22<br><!--Device-CURSOR_COPY = 14--><!--Device-CURSOR_COPY = 14-End--> |
| CURSOR_FORBID = 15 | Forbid<br>**Since**: 22<br><!--Device-CURSOR_FORBID = 15--><!--Device-CURSOR_FORBID = 15-End--> |
| COLOR_SUCKER = 16 | Color picker<br>**Since**: 22<br><!--Device-COLOR_SUCKER = 16--><!--Device-COLOR_SUCKER = 16-End--> |
| HAND_GRABBING = 17 | Grabbing hand<br>**Since**: 22<br><!--Device-HAND_GRABBING = 17--><!--Device-HAND_GRABBING = 17-End--> |
| HAND_OPEN = 18 | Opening hand<br>**Since**: 22<br><!--Device-HAND_OPEN = 18--><!--Device-HAND_OPEN = 18-End--> |
| HAND_POINTING = 19 | Hand-shaped pointer<br>**Since**: 22<br><!--Device-HAND_POINTING = 19--><!--Device-HAND_POINTING = 19-End--> |
| HELP = 20 | Help<br>**Since**: 22<br><!--Device-HELP = 20--><!--Device-HELP = 20-End--> |
| MOVE = 21 | Move<br>**Since**: 22<br><!--Device-MOVE = 21--><!--Device-MOVE = 21-End--> |
| RESIZE_LEFT_RIGHT = 22 | Left and right resizing<br>**Since**: 22<br><!--Device-RESIZE_LEFT_RIGHT = 22--><!--Device-RESIZE_LEFT_RIGHT = 22-End--> |
| RESIZE_UP_DOWN = 23 | Up and down resizing<br>**Since**: 22<br><!--Device-RESIZE_UP_DOWN = 23--><!--Device-RESIZE_UP_DOWN = 23-End--> |
| SCREENSHOT_CHOOSE = 24 | Screenshot crosshair<br>**Since**: 22<br><!--Device-SCREENSHOT_CHOOSE = 24--><!--Device-SCREENSHOT_CHOOSE = 24-End--> |
| SCREENSHOT_CURSOR = 25 | Screenshot<br>**Since**: 22<br><!--Device-SCREENSHOT_CURSOR = 25--><!--Device-SCREENSHOT_CURSOR = 25-End--> |
| TEXT_CURSOR = 26 | Text selection<br>**Since**: 22<br><!--Device-TEXT_CURSOR = 26--><!--Device-TEXT_CURSOR = 26-End--> |
| ZOOM_IN = 27 | Zoom in<br>**Since**: 22<br><!--Device-ZOOM_IN = 27--><!--Device-ZOOM_IN = 27-End--> |
| ZOOM_OUT = 28 | Zoom out<br>**Since**: 22<br><!--Device-ZOOM_OUT = 28--><!--Device-ZOOM_OUT = 28-End--> |
| MIDDLE_BTN_EAST = 29 | Scrolling east<br>**Since**: 22<br><!--Device-MIDDLE_BTN_EAST = 29--><!--Device-MIDDLE_BTN_EAST = 29-End--> |
| MIDDLE_BTN_WEST = 30 | Scrolling west<br>**Since**: 22<br><!--Device-MIDDLE_BTN_WEST = 30--><!--Device-MIDDLE_BTN_WEST = 30-End--> |
| MIDDLE_BTN_SOUTH = 31 | Scrolling south<br>**Since**: 22<br><!--Device-MIDDLE_BTN_SOUTH = 31--><!--Device-MIDDLE_BTN_SOUTH = 31-End--> |
| MIDDLE_BTN_NORTH = 32 | Scrolling north<br>**Since**: 22<br><!--Device-MIDDLE_BTN_NORTH = 32--><!--Device-MIDDLE_BTN_NORTH = 32-End--> |
| MIDDLE_BTN_NORTH_SOUTH = 33 | Scrolling north-south<br>**Since**: 22<br><!--Device-MIDDLE_BTN_NORTH_SOUTH = 33--><!--Device-MIDDLE_BTN_NORTH_SOUTH = 33-End--> |
| MIDDLE_BTN_NORTH_EAST = 34 | Scrolling north-east<br>**Since**: 22<br><!--Device-MIDDLE_BTN_NORTH_EAST = 34--><!--Device-MIDDLE_BTN_NORTH_EAST = 34-End--> |
| MIDDLE_BTN_NORTH_WEST = 35 | Scrolling north-west<br>**Since**: 22<br><!--Device-MIDDLE_BTN_NORTH_WEST = 35--><!--Device-MIDDLE_BTN_NORTH_WEST = 35-End--> |
| MIDDLE_BTN_SOUTH_EAST = 36 | Scrolling south-east<br>**Since**: 22<br><!--Device-MIDDLE_BTN_SOUTH_EAST = 36--><!--Device-MIDDLE_BTN_SOUTH_EAST = 36-End--> |
| MIDDLE_BTN_SOUTH_WEST = 37 | Scrolling south-west<br>**Since**: 22<br><!--Device-MIDDLE_BTN_SOUTH_WEST = 37--><!--Device-MIDDLE_BTN_SOUTH_WEST = 37-End--> |
| MIDDLE_BTN_NORTH_SOUTH_WEST_EAST = 38 | Moving as a cone in four directions<br>**Since**: 22<br><!--Device-MIDDLE_BTN_NORTH_SOUTH_WEST_EAST = 38--><!--Device-MIDDLE_BTN_NORTH_SOUTH_WEST_EAST = 38-End--> |
| HORIZONTAL_TEXT_CURSOR = 39 | Selecting text horizontally<br>**Since**: 22<br><!--Device-HORIZONTAL_TEXT_CURSOR = 39--><!--Device-HORIZONTAL_TEXT_CURSOR = 39-End--> |
| CURSOR_CROSS = 40 | Cross<br>**Since**: 22<br><!--Device-CURSOR_CROSS = 40--><!--Device-CURSOR_CROSS = 40-End--> |
| CURSOR_CIRCLE = 41 | Circle<br>**Since**: 22<br><!--Device-CURSOR_CIRCLE = 41--><!--Device-CURSOR_CIRCLE = 41-End--> |
| LOADING = 42 | Loading<br>**Since**: 22<br><!--Device-LOADING = 42--><!--Device-LOADING = 42-End--> |
| RUNNING = 43 | Running in the background<br>**Since**: 22<br><!--Device-RUNNING = 43--><!--Device-RUNNING = 43-End--> |
| MIDDLE_BTN_EAST_WEST = 44 | Scrolling east-west<br>**Since**: 22<br><!--Device-MIDDLE_BTN_EAST_WEST = 44--><!--Device-MIDDLE_BTN_EAST_WEST = 44-End--> |
| RUNNING_LEFT = 45 | Running in the background (extension 1)<br>**Since**: 22<br><!--Device-RUNNING_LEFT = 45--><!--Device-RUNNING_LEFT = 45-End--> |
| RUNNING_RIGHT = 46 | Running in the background (extension 2)<br>**Since**: 22<br><!--Device-RUNNING_RIGHT = 46--><!--Device-RUNNING_RIGHT = 46-End--> |
| AECH_DEVELOPER_DEFINED_ICON = 47 | Custom circular cursor<br>**Since**: 22<br><!--Device-AECH_DEVELOPER_DEFINED_ICON = 47--><!--Device-AECH_DEVELOPER_DEFINED_ICON = 47-End--> |
| SCREENRECORDER_CURSOR = 48 | Screen recording cursor<br>**Since**: 22<br><!--Device-SCREENRECORDER_CURSOR = 48--><!--Device-SCREENRECORDER_CURSOR = 48-End--> |
| LASER_CURSOR = 49 | Floating cursor. This cursor is used when the stylus enters air mouse mode and cannot be set directly.<br>In air mouse mode, the stylus can be rotated in the air to control the movement of the virtual cursor on the screen, and the buttons on the stylus body can be used to implement page up/down, for scenarios such as PPT presentations and air gesture operations.<br>**Since**: 22<br><!--Device-LASER_CURSOR = 49--><!--Device-LASER_CURSOR = 49-End--> |
| LASER_CURSOR_DOT = 50 | Click cursor. This cursor is used when the stylus enters air mouse mode and cannot be set directly.<br>In air mouse mode, the stylus can be rotated in the air to control the movement of the virtual cursor on the screen, and the buttons on the stylus body can be used to implement page up/down, for scenarios such as PPT presentations and air gesture operations.<br>**Since**: 22<br><!--Device-LASER_CURSOR_DOT = 50--><!--Device-LASER_CURSOR_DOT = 50-End--> |
| LASER_CURSOR_DOT_RED = 51 | Laser pointer cursor. This cursor is used when the stylus enters air mouse mode and cannot be set directly.<br>In air mouse mode, the stylus can be rotated in the air to control the movement of the virtual cursor on the screen, and the buttons on the stylus body can be used to implement page up/down, for scenarios such as PPT presentations and air gesture operations.<br>**Since**: 22<br><!--Device-LASER_CURSOR_DOT_RED = 51--><!--Device-LASER_CURSOR_DOT_RED = 51-End--> |
| DEVELOPER_DEFINED_ICON = -100 | Custom cursor. You can use the [OH_Input_SetCustomCursor](capi-oh-input-manager-h.md#oh_input_setcustomcursor) to set a custom cursor, but not the [OH_Input_SetPointerStyle](capi-oh-input-manager-h.md#oh_input_setpointerstyle).<br>**Since**: 22<br><!--Device-DEVELOPER_DEFINED_ICON = -100--><!--Device-DEVELOPER_DEFINED_ICON = -100-End--> |


