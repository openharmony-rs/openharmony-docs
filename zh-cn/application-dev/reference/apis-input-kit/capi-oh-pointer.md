# oh_pointer.h

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

鼠标光标样式枚举。

**引用文件：** <multimodalinput/oh_pointer.h>

**库：** libohinput.so

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**起始版本：** 22

**相关模块：** [input](capi-input.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Input_PointerStyle](#input_pointerstyle) | Input_PointerStyle | 鼠标光标样式。 |

## 枚举类型说明

### Input_PointerStyle

```
enum Input_PointerStyle
```

**描述**

鼠标光标样式。

**起始版本：** 22

鼠标样式类型。

| 名称                               | 值    | 说明     |图示 |
| -------------------------------- | ---- | ------ |------ |
| DEFAULT                          | 0    | 默认     |![Default.png](./figures/Default.png)|
| EAST                             | 1    | 向东箭头   |![East.png](./figures/East.png)|
| WEST                             | 2    | 向西箭头   |![West.png](./figures/West.png)|
| SOUTH                            | 3    | 向南箭头   |![South.png](./figures/South.png)|
| NORTH                            | 4    | 向北箭头   |![North.png](./figures/North.png)|
| WEST_EAST                        | 5    | 向西东箭头  |![West_East.png](./figures/West_East.png)|
| NORTH_SOUTH                      | 6    | 向北南箭头  |![North_South.png](./figures/North_South.png)|
| NORTH_EAST                       | 7    | 向东北箭头  |![North_East.png](./figures/North_East.png)|
| NORTH_WEST                       | 8    | 向西北箭头  |![North_West.png](./figures/North_West.png)|
| SOUTH_EAST                       | 9    | 向东南箭头  |![South_East.png](./figures/South_East.png)|
| SOUTH_WEST                       | 10   | 向西南箭头  |![South_West.png](./figures/South_West.png)|
| NORTH_EAST_SOUTH_WEST            | 11   | 东北西南调整 |![North_East_South_West.png](./figures/North_East_South_West.png)|
| NORTH_WEST_SOUTH_EAST            | 12   | 西北东南调整 |![North_West_South_East.png](./figures/North_West_South_East.png)|
| CROSS                            | 13   | 准确选择   |![Cross.png](./figures/Cross.png)|
| CURSOR_COPY                      | 14   | 拷贝     |![Copy.png](./figures/Copy.png)|
| CURSOR_FORBID                    | 15   | 不可用    |![Forbid.png](./figures/Forbid.png)|
| COLOR_SUCKER                     | 16   | 滴管     |![Colorsucker.png](./figures/Colorsucker.png)|
| HAND_GRABBING                    | 17   | 并拢的手   |![Hand_Grabbing.png](./figures/Hand_Grabbing.png)|
| HAND_OPEN                        | 18   | 张开的手   |![Hand_Open.png](./figures/Hand_Open.png)|
| HAND_POINTING                    | 19   | 手形指针   |![Hand_Poniting.png](./figures/Hand_Pointing.png)|
| HELP                             | 20   | 帮助选择   |![Help.png](./figures/Help.png)|
| MOVE                             | 21   | 移动     |![Move.png](./figures/Move.png)|
| RESIZE_LEFT_RIGHT                | 22   | 内部左右调整 |![Resize_Left_Right.png](./figures/Resize_Left_Right.png)|
| RESIZE_UP_DOWN                   | 23   | 内部上下调整 |![Resize_Up_Down.png](./figures/Resize_Up_Down.png)|
| SCREENSHOT_CHOOSE                | 24   | 截图十字准星 |![Screenshot_Cross.png](./figures/Screenshot_Cross.png)|
| SCREENSHOT_CURSOR                | 25   | 截图     |![Screenshot_Cursor.png](./figures/Screenshot_Cursor.png)|
| TEXT_CURSOR                      | 26   | 文本选择   |![Text_Cursor.png](./figures/Text_Cursor.png)|
| ZOOM_IN                          | 27   | 放大     |![Zoom_In.png](./figures/Zoom_In.png)|
| ZOOM_OUT                         | 28   | 缩小     |![Zoom_Out.png](./figures/Zoom_Out.png)|
| MIDDLE_BTN_EAST                  | 29   | 向东滚动   |![MID_Btn_East.png](./figures/MID_Btn_East.png)|
| MIDDLE_BTN_WEST                  | 30   | 向西滚动   |![MID_Btn_West.png](./figures/MID_Btn_West.png)|
| MIDDLE_BTN_SOUTH                 | 31   | 向南滚动   | ![MID_Btn_South.png](./figures/MID_Btn_South.png)|
| MIDDLE_BTN_NORTH                 | 32   | 向北滚动   |![MID_Btn_North.png](./figures/MID_Btn_North.png)|
| MIDDLE_BTN_NORTH_SOUTH           | 33   | 向南北滚动  |![MID_Btn_North_South.png](./figures/MID_Btn_North_South.png)|
| MIDDLE_BTN_NORTH_EAST            | 34   | 向东北滚动  |![MID_Btn_North_East.png](./figures/MID_Btn_North_East.png)|
| MIDDLE_BTN_NORTH_WEST            | 35   | 向西北滚动  |![MID_Btn_North_West.png](./figures/MID_Btn_North_West.png)|
| MIDDLE_BTN_SOUTH_EAST            | 36   | 向东南滚动  |![MID_Btn_South_East.png](./figures/MID_Btn_South_East.png)|
| MIDDLE_BTN_SOUTH_WEST            | 37   | 向西南滚动  |![MID_Btn_South_West.png](./figures/MID_Btn_South_West.png)|
| MIDDLE_BTN_NORTH_SOUTH_WEST_EAST | 38   | 四向锥形移动 |![MID_Btn_North_South_West_East.png](./figures/MID_Btn_North_South_West_East.png)|
| HORIZONTAL_TEXT_CURSOR | 39 | 垂直文本选择 |![Horizontal_Text_Cursor.png](./figures/Horizontal_Text_Cursor.png)|
| CURSOR_CROSS | 40 | 十字光标 |![Cursor_Cross.png](./figures/Cursor_Cross.png)|
| CURSOR_CIRCLE | 41 | 圆形光标 |![Cursor_Circle.png](./figures/Cursor_Circle.png)|
| LOADING | 42 | 正在载入动画光标 |![Loading.png](./figures/Loading.png)|
| RUNNING | 43 | 后台运行中动画光标 |![Running.png](./figures/Running.png)|
| MIDDLE_BTN_EAST_WEST          | 44   | 向东西滚动 |![MID_Btn_East_West.png](./figures/MID_Btn_East_West.png)|
| SCREENRECORDER_CURSOR        | 48   | 录屏光标  |![ScreenRecorder_Cursor.png](./figures/ScreenRecorder_Cursor.png)|


