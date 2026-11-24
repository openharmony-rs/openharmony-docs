# oh_pointer_style.h

## 概述

鼠标光标的样式。

**引用文件：** <multimodalinput/oh_pointer_style.h>

**库：** libohinput.so

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**起始版本：** 22

**相关模块：** [input](capi-input-kit-input.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Input_PointerStyle](#input_pointerstyle) | Input_PointerStyle | 鼠标光标样式。 |

## 枚举类型说明

### Input_PointerStyle

```c
enum Input_PointerStyle
```

**描述：**

鼠标光标样式。

<!--Device-enum Input_PointerStyle--><!--Device-enum Input_PointerStyle-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| DEFAULT = 0 | 应用未设置时显示的光标样式。<br>**起始版本：** 22<br><!--Device-DEFAULT = 0--><!--Device-DEFAULT = 0-End--> |
| EAST = 1 | 向东箭头<br>**起始版本：** 22<br><!--Device-EAST = 1--><!--Device-EAST = 1-End--> |
| WEST = 2 | 向西箭头<br>**起始版本：** 22<br><!--Device-WEST = 2--><!--Device-WEST = 2-End--> |
| SOUTH = 3 | 向南箭头<br>**起始版本：** 22<br><!--Device-SOUTH = 3--><!--Device-SOUTH = 3-End--> |
| NORTH = 4 | 向北箭头<br>**起始版本：** 22<br><!--Device-NORTH = 4--><!--Device-NORTH = 4-End--> |
| WEST_EAST = 5 | 向西东箭头<br>**起始版本：** 22<br><!--Device-WEST_EAST = 5--><!--Device-WEST_EAST = 5-End--> |
| NORTH_SOUTH = 6 | 向北南箭头<br>**起始版本：** 22<br><!--Device-NORTH_SOUTH = 6--><!--Device-NORTH_SOUTH = 6-End--> |
| NORTH_EAST = 7 | 向东北箭头<br>**起始版本：** 22<br><!--Device-NORTH_EAST = 7--><!--Device-NORTH_EAST = 7-End--> |
| NORTH_WEST = 8 | 向西北箭头<br>**起始版本：** 22<br><!--Device-NORTH_WEST = 8--><!--Device-NORTH_WEST = 8-End--> |
| SOUTH_EAST = 9 | 向东南箭头<br>**起始版本：** 22<br><!--Device-SOUTH_EAST = 9--><!--Device-SOUTH_EAST = 9-End--> |
| SOUTH_WEST = 10 | 向西南箭头<br>**起始版本：** 22<br><!--Device-SOUTH_WEST = 10--><!--Device-SOUTH_WEST = 10-End--> |
| NORTH_EAST_SOUTH_WEST = 11 | 东北西南调整<br>**起始版本：** 22<br><!--Device-NORTH_EAST_SOUTH_WEST = 11--><!--Device-NORTH_EAST_SOUTH_WEST = 11-End--> |
| NORTH_WEST_SOUTH_EAST = 12 | 西北东南调整<br>**起始版本：** 22<br><!--Device-NORTH_WEST_SOUTH_EAST = 12--><!--Device-NORTH_WEST_SOUTH_EAST = 12-End--> |
| CROSS = 13 | 准确选择<br>**起始版本：** 22<br><!--Device-CROSS = 13--><!--Device-CROSS = 13-End--> |
| CURSOR_COPY = 14 | 复制<br>**起始版本：** 22<br><!--Device-CURSOR_COPY = 14--><!--Device-CURSOR_COPY = 14-End--> |
| CURSOR_FORBID = 15 | 不可用<br>**起始版本：** 22<br><!--Device-CURSOR_FORBID = 15--><!--Device-CURSOR_FORBID = 15-End--> |
| COLOR_SUCKER = 16 | 取色器<br>**起始版本：** 22<br><!--Device-COLOR_SUCKER = 16--><!--Device-COLOR_SUCKER = 16-End--> |
| HAND_GRABBING = 17 | 并拢的手<br>**起始版本：** 22<br><!--Device-HAND_GRABBING = 17--><!--Device-HAND_GRABBING = 17-End--> |
| HAND_OPEN = 18 | 张开的手<br>**起始版本：** 22<br><!--Device-HAND_OPEN = 18--><!--Device-HAND_OPEN = 18-End--> |
| HAND_POINTING = 19 | 手形指针<br>**起始版本：** 22<br><!--Device-HAND_POINTING = 19--><!--Device-HAND_POINTING = 19-End--> |
| HELP = 20 | 帮助选择<br>**起始版本：** 22<br><!--Device-HELP = 20--><!--Device-HELP = 20-End--> |
| MOVE = 21 | 移动<br>**起始版本：** 22<br><!--Device-MOVE = 21--><!--Device-MOVE = 21-End--> |
| RESIZE_LEFT_RIGHT = 22 | 内部左右调整<br>**起始版本：** 22<br><!--Device-RESIZE_LEFT_RIGHT = 22--><!--Device-RESIZE_LEFT_RIGHT = 22-End--> |
| RESIZE_UP_DOWN = 23 | 内部上下调整<br>**起始版本：** 22<br><!--Device-RESIZE_UP_DOWN = 23--><!--Device-RESIZE_UP_DOWN = 23-End--> |
| SCREENSHOT_CHOOSE = 24 | 截图十字准星<br>**起始版本：** 22<br><!--Device-SCREENSHOT_CHOOSE = 24--><!--Device-SCREENSHOT_CHOOSE = 24-End--> |
| SCREENSHOT_CURSOR = 25 | 截图<br>**起始版本：** 22<br><!--Device-SCREENSHOT_CURSOR = 25--><!--Device-SCREENSHOT_CURSOR = 25-End--> |
| TEXT_CURSOR = 26 | 文本选择<br>**起始版本：** 22<br><!--Device-TEXT_CURSOR = 26--><!--Device-TEXT_CURSOR = 26-End--> |
| ZOOM_IN = 27 | 放大<br>**起始版本：** 22<br><!--Device-ZOOM_IN = 27--><!--Device-ZOOM_IN = 27-End--> |
| ZOOM_OUT = 28 | 缩小<br>**起始版本：** 22<br><!--Device-ZOOM_OUT = 28--><!--Device-ZOOM_OUT = 28-End--> |
| MIDDLE_BTN_EAST = 29 | 向东滚动<br>**起始版本：** 22<br><!--Device-MIDDLE_BTN_EAST = 29--><!--Device-MIDDLE_BTN_EAST = 29-End--> |
| MIDDLE_BTN_WEST = 30 | 向西滚动<br>**起始版本：** 22<br><!--Device-MIDDLE_BTN_WEST = 30--><!--Device-MIDDLE_BTN_WEST = 30-End--> |
| MIDDLE_BTN_SOUTH = 31 | 向南滚动<br>**起始版本：** 22<br><!--Device-MIDDLE_BTN_SOUTH = 31--><!--Device-MIDDLE_BTN_SOUTH = 31-End--> |
| MIDDLE_BTN_NORTH = 32 | 向北滚动<br>**起始版本：** 22<br><!--Device-MIDDLE_BTN_NORTH = 32--><!--Device-MIDDLE_BTN_NORTH = 32-End--> |
| MIDDLE_BTN_NORTH_SOUTH = 33 | 向南北滚动<br>**起始版本：** 22<br><!--Device-MIDDLE_BTN_NORTH_SOUTH = 33--><!--Device-MIDDLE_BTN_NORTH_SOUTH = 33-End--> |
| MIDDLE_BTN_NORTH_EAST = 34 | 向东北滚动<br>**起始版本：** 22<br><!--Device-MIDDLE_BTN_NORTH_EAST = 34--><!--Device-MIDDLE_BTN_NORTH_EAST = 34-End--> |
| MIDDLE_BTN_NORTH_WEST = 35 | 向西北滚动<br>**起始版本：** 22<br><!--Device-MIDDLE_BTN_NORTH_WEST = 35--><!--Device-MIDDLE_BTN_NORTH_WEST = 35-End--> |
| MIDDLE_BTN_SOUTH_EAST = 36 | 向东南滚动<br>**起始版本：** 22<br><!--Device-MIDDLE_BTN_SOUTH_EAST = 36--><!--Device-MIDDLE_BTN_SOUTH_EAST = 36-End--> |
| MIDDLE_BTN_SOUTH_WEST = 37 | 向西南滚动<br>**起始版本：** 22<br><!--Device-MIDDLE_BTN_SOUTH_WEST = 37--><!--Device-MIDDLE_BTN_SOUTH_WEST = 37-End--> |
| MIDDLE_BTN_NORTH_SOUTH_WEST_EAST = 38 | 四向锥形移动<br>**起始版本：** 22<br><!--Device-MIDDLE_BTN_NORTH_SOUTH_WEST_EAST = 38--><!--Device-MIDDLE_BTN_NORTH_SOUTH_WEST_EAST = 38-End--> |
| HORIZONTAL_TEXT_CURSOR = 39 | 水平文本选择<br>**起始版本：** 22<br><!--Device-HORIZONTAL_TEXT_CURSOR = 39--><!--Device-HORIZONTAL_TEXT_CURSOR = 39-End--> |
| CURSOR_CROSS = 40 | 十字光标<br>**起始版本：** 22<br><!--Device-CURSOR_CROSS = 40--><!--Device-CURSOR_CROSS = 40-End--> |
| CURSOR_CIRCLE = 41 | 圆形光标<br>**起始版本：** 22<br><!--Device-CURSOR_CIRCLE = 41--><!--Device-CURSOR_CIRCLE = 41-End--> |
| LOADING = 42 | 正在载入动画光标<br>**起始版本：** 22<br><!--Device-LOADING = 42--><!--Device-LOADING = 42-End--> |
| RUNNING = 43 | 后台运行中动画光标<br>**起始版本：** 22<br><!--Device-RUNNING = 43--><!--Device-RUNNING = 43-End--> |
| MIDDLE_BTN_EAST_WEST = 44 | 向东西滚动<br>**起始版本：** 22<br><!--Device-MIDDLE_BTN_EAST_WEST = 44--><!--Device-MIDDLE_BTN_EAST_WEST = 44-End--> |
| RUNNING_LEFT = 45 | 后台运行中动画光标（拓展1）<br>**起始版本：** 22<br><!--Device-RUNNING_LEFT = 45--><!--Device-RUNNING_LEFT = 45-End--> |
| RUNNING_RIGHT = 46 | 后台运行中动画光标（拓展2）<br>**起始版本：** 22<br><!--Device-RUNNING_RIGHT = 46--><!--Device-RUNNING_RIGHT = 46-End--> |
| AECH_DEVELOPER_DEFINED_ICON = 47 | 圆形自定义光标<br>**起始版本：** 22<br><!--Device-AECH_DEVELOPER_DEFINED_ICON = 47--><!--Device-AECH_DEVELOPER_DEFINED_ICON = 47-End--> |
| SCREENRECORDER_CURSOR = 48 | 录屏光标<br>**起始版本：** 22<br><!--Device-SCREENRECORDER_CURSOR = 48--><!--Device-SCREENRECORDER_CURSOR = 48-End--> |
| LASER_CURSOR = 49 | 悬浮光标。手写笔进入空鼠模式时使用该光标，无法直接设置。<br>空鼠模式支持通过手写笔在空中转动来控制屏幕上虚拟光标的移动，并借助笔身按键实现上下翻页功能，用于演示PPT、隔空操作等场景。<br>**起始版本：** 22<br><!--Device-LASER_CURSOR = 49--><!--Device-LASER_CURSOR = 49-End--> |
| LASER_CURSOR_DOT = 50 | 点击光标。手写笔进入空鼠模式时使用该光标，无法直接设置。<br>空鼠模式支持通过手写笔在空中转动来控制屏幕上虚拟光标的移动，并借助笔身按键实现上下翻页功能，用于演示PPT、隔空操作等场景。<br>**起始版本：** 22<br><!--Device-LASER_CURSOR_DOT = 50--><!--Device-LASER_CURSOR_DOT = 50-End--> |
| LASER_CURSOR_DOT_RED = 51 | 激光笔光标。手写笔进入空鼠模式时使用该光标，无法直接设置。<br>空鼠模式支持通过手写笔在空中转动来控制屏幕上虚拟光标的移动，并借助笔身按键实现上下翻页功能，用于演示PPT、隔空操作等场景。<br>**起始版本：** 22<br><!--Device-LASER_CURSOR_DOT_RED = 51--><!--Device-LASER_CURSOR_DOT_RED = 51-End--> |
| DEVELOPER_DEFINED_ICON = -100 | 自定义光标，开发者可使用[OH_Input_SetCustomCursor](capi-oh-input-manager-h.md#oh_input_setcustomcursor)设置自定义光标， 不支持使用[OH_Input_SetPointerStyle](capi-oh-input-manager-h.md#oh_input_setpointerstyle)直接设置。<br>**起始版本：** 22<br><!--Device-DEVELOPER_DEFINED_ICON = -100--><!--Device-DEVELOPER_DEFINED_ICON = -100-End--> |


