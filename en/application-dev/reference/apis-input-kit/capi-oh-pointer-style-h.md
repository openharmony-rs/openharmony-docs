# oh_pointer_style.h

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines the mouse pointer styles.

**File to include**: <multimodalinput/oh_pointer_style.h>

**Library**: libohinput.so

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 22

**Related module**: [input](capi-input.md)

## Summary

### Enums

| API| typedef Keyword| Description|
| -- | -- | -- |
| [Input_PointerStyle](#input_pointerstyle) | Input_PointerStyle | Pointer style.|

## Enum Description

### Input_PointerStyle

```c
enum Input_PointerStyle
```

**Description**

Enumerates the pointer styles.

**Since**: 22

| Name                              | Value   | Description    |Legend|
| -------------------------------- | ---- | ------ |------ |
| DEFAULT                          | 0    | Default     |![Default.png](./figures/Default.png)|
| EAST                             | 1    | East arrow  |![East.png](./figures/East.png)|
| WEST                             | 2    | West arrow  |![West.png](./figures/West.png)|
| SOUTH                            | 3    | South arrow  |![South.png](./figures/South.png)|
| NORTH                            | 4    | North arrow  |![North.png](./figures/North.png)|
| WEST_EAST                        | 5    | West-east arrow |![West_East.png](./figures/West_East.png)|
| NORTH_SOUTH                      | 6    | North-south arrow |![North_South.png](./figures/North_South.png)|
| NORTH_EAST                       | 7    | North-east arrow |![North_East.png](./figures/North_East.png)|
| NORTH_WEST                       | 8    | North-west arrow |![North_West.png](./figures/North_West.png)|
| SOUTH_EAST                       | 9    | South-east arrow |![South_East.png](./figures/South_East.png)|
| SOUTH_WEST                       | 10   | South-west arrow |![South_West.png](./figures/South_West.png)|
| NORTH_EAST_SOUTH_WEST            | 11   | North-east and south-west adjustment|![North_East_South_West.png](./figures/North_East_South_West.png)|
| NORTH_WEST_SOUTH_EAST            | 12   | North-west and south-east adjustment|![North_West_South_East.png](./figures/North_West_South_East.png)|
| CROSS                            | 13   | Cross (accurate selection)  |![Cross.png](./figures/Cross.png)|
| CURSOR_COPY                      | 14   | Copy    |![Copy.png](./figures/Copy.png)|
| CURSOR_FORBID                    | 15   | Forbid   |![Forbid.png](./figures/Forbid.png)|
| COLOR_SUCKER                     | 16   | Sucker    |![Colorsucker.png](./figures/Colorsucker.png)|
| HAND_GRABBING                    | 17   | Grabbing hand  |![Hand_Grabbing.png](./figures/Hand_Grabbing.png)|
| HAND_OPEN                        | 18   | Opening hand  |![Hand_Open.png](./figures/Hand_Open.png)|
| HAND_POINTING                    | 19   | Hand-shaped pointer  |![Hand_Pointing.png](./figures/Hand_Pointing.png)|
| HELP                             | 20   | Help   |![Help.png](./figures/Help.png)|
| MOVE                             | 21   | Move    |![Move.png](./figures/Move.png)|
| RESIZE_LEFT_RIGHT                | 22   | Left and right resizing|![Resize_Left_Right.png](./figures/Resize_Left_Right.png)|
| RESIZE_UP_DOWN                   | 23   | Up and down resizing|![Resize_Up_Down.png](./figures/Resize_Up_Down.png)|
| SCREENSHOT_CHOOSE                | 24   | Screenshot crosshair|![Screenshot_Cross.png](./figures/Screenshot_Cross.png)|
| SCREENSHOT_CURSOR                | 25   | Screenshot    |![Screenshot_Cursor.png](./figures/Screenshot_Cursor.png)|
| TEXT_CURSOR                      | 26   | Text selection  |![Text_Cursor.png](./figures/Text_Cursor.png)|
| ZOOM_IN                          | 27   | Zoom in    |![Zoom_In.png](./figures/Zoom_In.png)|
| ZOOM_OUT                         | 28   | Zoom out    |![Zoom_Out.png](./figures/Zoom_Out.png)|
| MIDDLE_BTN_EAST                  | 29   | Scrolling east  |![MID_Btn_East.png](./figures/MID_Btn_East.png)|
| MIDDLE_BTN_WEST                  | 30   | Scrolling west  |![MID_Btn_West.png](./figures/MID_Btn_West.png)|
| MIDDLE_BTN_SOUTH                 | 31   | Scrolling south  | ![MID_Btn_South.png](./figures/MID_Btn_South.png)|
| MIDDLE_BTN_NORTH                 | 32   | Scrolling north  |![MID_Btn_North.png](./figures/MID_Btn_North.png)|
| MIDDLE_BTN_NORTH_SOUTH           | 33   | Scrolling north-south |![MID_Btn_North_South.png](./figures/MID_Btn_North_South.png)|
| MIDDLE_BTN_NORTH_EAST            | 34   | Scrolling north-east |![MID_Btn_North_East.png](./figures/MID_Btn_North_East.png)|
| MIDDLE_BTN_NORTH_WEST            | 35   | Scrolling north-west |![MID_Btn_North_West.png](./figures/MID_Btn_North_West.png)|
| MIDDLE_BTN_SOUTH_EAST            | 36   | Scrolling south-east |![MID_Btn_South_East.png](./figures/MID_Btn_South_East.png)|
| MIDDLE_BTN_SOUTH_WEST            | 37   | Scrolling south-west |![MID_Btn_South_West.png](./figures/MID_Btn_South_West.png)|
| MIDDLE_BTN_NORTH_SOUTH_WEST_EAST | 38   | Moving as a cone in four directions|![MID_Btn_North_South_West_East.png](./figures/MID_Btn_North_South_West_East.png)|
| HORIZONTAL_TEXT_CURSOR | 39 | Horizontal text selection|![Horizontal_Text_Cursor.png](./figures/Horizontal_Text_Cursor.png)|
| CURSOR_CROSS | 40 | Cross|![Cursor_Cross.png](./figures/Cursor_Cross.png)|
| CURSOR_CIRCLE | 41 | Circle|![Cursor_Circle.png](./figures/Cursor_Circle.png)|
| LOADING | 42 | Loading|![Loading.png](./figures/Loading.png)|
| RUNNING | 43 | Running in the background|![Running.png](./figures/Running.png)|
| MIDDLE_BTN_EAST_WEST         | 44   | Scrolling east-west|![MID_Btn_East_West.png](./figures/MID_Btn_East_West.png)|
| RUNNING_LEFT         | 45   | Running in the background (extension 1)|![Loading_Left.png](./figures/Loading_Left.png)|
| RUNNING_RIGHT         | 46   | Running in the background (extension 2)|![Loading_Right.png](./figures/Loading_Right.png)|
| AECH_DEVELOPER_DEFINED_ICON         | 47   | Custom circular pointer|![Custom_Cursor_Circle.png](./figures/Custom_Cursor_Circle.png)|
| SCREENRECORDER_CURSOR        | 48   | Screen recording |![ScreenRecorder_Cursor.png](./figures/ScreenRecorder_Cursor.png)|
| LASER_CURSOR        | 49   | Floating This pointer can be used only when the stylus enters the air mouse mode.<br>In air mouse mode, you can rotate the stylus in the air to control the movement of the virtual pointer on the screen and press the button on the stylus to turn pages up or down. This mode is used PPT presentation and air gesture control.|![Laser_Cursor.png](./figures/Laser_Cursor.png)|
| LASER_CURSOR_DOT        | 50   | Click This pointer can be used only when the stylus enters the air mouse mode.<br>In air mouse mode, you can rotate the stylus in the air to control the movement of the virtual pointer on the screen and press the button on the stylus to turn pages up or down. This mode is used PPT presentation and air gesture control.|![Laser_Cursor_Dot.png](./figures/Laser_Cursor_Dot.png)|
| LASER_CURSOR_DOT_RED        | 51   | Laser pointer This pointer can be used only when the stylus enters the air mouse mode.<br>In air mouse mode, you can rotate the stylus in the air to control the movement of the virtual pointer on the screen and press the button on the stylus to turn pages up or down. This mode is used PPT presentation and air gesture control.|![Laser_Cursor_Dot_Red.png](./figures/Laser_Cursor_Dot_Red.png)|
| DEVELOPER_DEFINED_ICON        | -100 | Custom pointer. You can use the [OH_Input_SetCustomCursor](./capi-oh-input-manager-h.md#oh_input_setcustomcursor) to set a custom pointer, but not the [OH_Input_SetPointerStyle](./capi-oh-input-manager-h.md#oh_input_setpointerstyle).|You can customize pointers as needed via API.|
