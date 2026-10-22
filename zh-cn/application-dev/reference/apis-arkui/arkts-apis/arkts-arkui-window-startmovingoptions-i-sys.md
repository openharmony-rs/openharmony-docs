# StartMovingOptions（系统接口）

```TypeScript
interface StartMovingOptions
```

`startMovingWithOptions` 的可选配置。

**起始版本：** 26.0.0

<!--Device-window-interface StartMovingOptions--><!--Device-window-interface StartMovingOptions-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## avoidRect

```TypeScript
avoidRect?: Rect
```

窗口在拖拽移动过程中的避让区域。若未明确指定，系统将采用以下默认避让行为：自由窗口状态：
1. 主窗口、子窗口和对话框窗口可被拖拽至屏幕边界之外，
且在松开鼠标/手指后会自动回弹。
2. 其他类型的窗口可被拖拽至屏幕边界之外，且不会回弹。
非自由窗口状态：
1. 系统窗口可被拖拽至主窗口边界或屏幕边界之外，且不会回弹。
2. 当主窗口处于全屏状态时，
子窗口和对话框窗口可被拖拽至主窗口边界之外，且不会回弹。
3. 当主窗口未处于全屏状态时，
子窗口和对话框窗口可被拖拽至主窗口边界之外，且在松开鼠标/手指后会自动回弹。

**类型：** [Rect](arkts-arkui-window-rect-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartMovingOptions-avoidRect?: Rect--><!--Device-StartMovingOptions-avoidRect?: Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## needFocused

```TypeScript
needFocused?: boolean
```

指示在移动开始时窗口是否需要获取焦点。

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartMovingOptions-needFocused?: boolean--><!--Device-StartMovingOptions-needFocused?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。
