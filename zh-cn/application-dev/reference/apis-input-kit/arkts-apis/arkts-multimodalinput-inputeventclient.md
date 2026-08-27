# @ohos.multimodalInput.inputEventClient(输入事件注入)

输入事件注入模块，提供输入按键、鼠标/触控板、触屏输入事件注入能力。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createKeyboardController(输入事件注入)](arkts-input-inputeventclient-createkeyboardcontroller-f.md) | 创建键盘控制器，用于模拟按键操作。使用Promise异步回调。 |
| [createMouseController(输入事件注入)](arkts-input-inputeventclient-createmousecontroller-f.md) | 创建鼠标控制器，用于模拟鼠标操作。使用Promise异步回调。 |
| [createTouchController(输入事件注入)](arkts-input-inputeventclient-createtouchcontroller-f.md) | 创建触控控制器，用于模拟触控操作。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [injectEvent(输入事件注入)](arkts-input-inputeventclient-injectevent-f-sys.md) | 按键(包括单个按键和组合键)注入。 |
| [injectKeyEvent(输入事件注入)](arkts-input-inputeventclient-injectkeyevent-f-sys.md) | 按键(包括单个按键和组合键)事件注入。 |
| [injectMouseEvent(输入事件注入)](arkts-input-inputeventclient-injectmouseevent-f-sys.md) | 鼠标/触控板事件注入。 |
| [injectTouchEvent(输入事件注入)](arkts-input-inputeventclient-injecttouchevent-f-sys.md) | 触屏输入事件注入。 |
| [permitInjection(输入事件注入)](arkts-input-inputeventclient-permitinjection-f-sys.md) | 允许事件注入权限。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [KeyboardController(输入事件注入)](arkts-input-inputeventclient-keyboardcontroller-i.md) | 提供模拟按键操作的功能。模拟按键操作序列必须满足以下要求： 1. 按键只能在抬起状态下被按下，或者在该按键是最近按下的按键且未抬起的情况下被按下。 2. 按键只能在被按下后才能抬起。 3. 最多可以同时按下并保持五个按键。 |
| [MouseController(输入事件注入)](arkts-input-inputeventclient-mousecontroller-i.md) | 提供模拟鼠标操作的功能。模拟鼠标操作序列必须满足以下要求： 1. 鼠标按键只能在抬起状态下被按下。 2. 鼠标按键只能在被按下后才能抬起。 3. 有效的轴事件序列必须先调用beginAxis开始事件，然后调用零次或多次updateAxis更新事件，最后调用endAxis结束事件。 |
| [TouchController(输入事件注入)](arkts-input-inputeventclient-touchcontroller-i.md) | 提供模拟触控操作的功能。模拟触控操作序列必须满足以下要求： 1. 所有触点的displayId必须相同。 2. 每个触点都必须以`touchDown()`开始，以`touchUp()`结束，中间可包含多个`touchMove()`。 |
| [TouchPoint(输入事件注入)](arkts-input-inputeventclient-touchpoint-i.md) | 表示屏幕上的单个触点信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyEvent(输入事件注入)](arkts-input-inputeventclient-keyevent-i-sys.md) | 按键注入描述信息。 |
| [KeyEventData(输入事件注入)](arkts-input-inputeventclient-keyeventdata-i-sys.md) | 按键注入描述信息。 |
| [KeyEventInfo(输入事件注入)](arkts-input-inputeventclient-keyeventinfo-i-sys.md) | 定义用户注入的按键事件信息。 |
| [MouseEventData(输入事件注入)](arkts-input-inputeventclient-mouseeventdata-i-sys.md) | 鼠标注入描述信息。 |
| [TouchEventData(输入事件注入)](arkts-input-inputeventclient-toucheventdata-i-sys.md) | 触屏注入描述信息。 |
<!--DelEnd-->
