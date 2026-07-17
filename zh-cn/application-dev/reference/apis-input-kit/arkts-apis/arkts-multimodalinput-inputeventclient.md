# @ohos.multimodalInput.inputEventClient

输入事件注入模块，提供输入按键、鼠标/触控板、触屏输入事件注入能力。

> **说明：**  
>  
> - 本模块接口为系统接口。

**起始版本：** 26.0.0

<!--Device-unnamed-declare namespace inputEventClient--><!--Device-unnamed-declare namespace inputEventClient-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createKeyboardController](arkts-input-inputeventclient-createkeyboardcontroller-f.md#createkeyboardcontroller-1) | 创建键盘控制器，用于模拟按键操作。使用Promise异步回调。 |
| [createMouseController](arkts-input-inputeventclient-createmousecontroller-f.md#createmousecontroller-1) | 创建鼠标控制器，用于模拟鼠标操作。使用Promise异步回调。 |
| [createTouchController](arkts-input-inputeventclient-createtouchcontroller-f.md#createtouchcontroller-1) | 创建触控控制器，用于模拟触控操作。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [injectEvent](arkts-input-inputeventclient-injectevent-f-sys.md#injectevent-1) | 按键(包括单个按键和组合键)注入。 |
| [injectKeyEvent](arkts-input-inputeventclient-injectkeyevent-f-sys.md#injectkeyevent-1) | 按键(包括单个按键和组合键)事件注入。 |
| [injectMouseEvent](arkts-input-inputeventclient-injectmouseevent-f-sys.md#injectmouseevent-1) | 鼠标/触控板事件注入。 |
| [injectTouchEvent](arkts-input-inputeventclient-injecttouchevent-f-sys.md#injecttouchevent-1) | 触屏输入事件注入。 |
| [permitInjection](arkts-input-inputeventclient-permitinjection-f-sys.md#permitinjection-1) | 允许事件注入权限。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [KeyboardController](arkts-input-inputeventclient-keyboardcontroller-i.md) | 提供模拟按键操作的功能。模拟按键操作序列必须满足以下要求：1. 按键只能在抬起状态下被按下，或者在该按键是最近按下的按键且未抬起的情况下被按下。2. 按键只能在被按下后才能抬起。3. 最多可以同时按下并保持五个按键。 |
| [MouseController](arkts-input-inputeventclient-mousecontroller-i.md) | 提供模拟鼠标操作的功能。模拟鼠标操作序列必须满足以下要求：1. 鼠标按键只能在抬起状态下被按下。2. 鼠标按键只能在被按下后才能抬起。3. 有效的轴事件序列必须先调用beginAxis开始事件，然后调用零次或多次updateAxis更新事件，最后调用endAxis结束事件。4. 同一时间只能有一个进行中的轴事件序列。 |
| [TouchController](arkts-input-inputeventclient-touchcontroller-i.md) | 提供模拟触控操作的功能。模拟触控操作序列必须满足以下要求：1. 所有触点的displayId必须相同。2. 每个触点都必须以`touchDown()`开始，以`touchUp()`结束，中间可包含多个`touchMove()`。 |
| [TouchPoint](arkts-input-inputeventclient-touchpoint-i.md) | 表示屏幕上的单个触点信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyEvent](arkts-input-inputeventclient-keyevent-i-sys.md) | 按键注入描述信息。 |
| [KeyEventData](arkts-input-inputeventclient-keyeventdata-i-sys.md) | 按键注入描述信息。 |
| [KeyEventInfo](arkts-input-inputeventclient-keyeventinfo-i-sys.md) | 定义用户注入的按键事件信息。 |
| [MouseEventData](arkts-input-inputeventclient-mouseeventdata-i-sys.md) | 鼠标注入描述信息。 |
| [TouchEventData](arkts-input-inputeventclient-toucheventdata-i-sys.md) | 触屏注入描述信息。 |
<!--DelEnd-->

