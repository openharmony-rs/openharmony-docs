# AccessibilityAction（系统接口）

表示无障碍节点元素可执行的操作枚举。 无障碍节点元素是指，UI界面上可执行无障碍操作的组件，例如：按钮、文本输入框等。

**起始版本：** 23

<!--Device-unnamed-export enum AccessibilityAction--><!--Device-unnamed-export enum AccessibilityAction-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## ACCESSIBILITY_FOCUS

```TypeScript
ACCESSIBILITY_FOCUS = 0
```

表示获得无障碍焦点。需配置参数[Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).accessibilityFocusScene，参数值 为无障碍聚焦的场景类型。

**起始版本：** 23

<!--Device-AccessibilityAction-ACCESSIBILITY_FOCUS = 0--><!--Device-AccessibilityAction-ACCESSIBILITY_FOCUS = 0-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## CLEAR_ACCESSIBILITY_FOCUS

```TypeScript
CLEAR_ACCESSIBILITY_FOCUS = 1
```

表示清除无障碍焦点。

**起始版本：** 23

<!--Device-AccessibilityAction-CLEAR_ACCESSIBILITY_FOCUS = 1--><!--Device-AccessibilityAction-CLEAR_ACCESSIBILITY_FOCUS = 1-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## FOCUS

```TypeScript
FOCUS = 2
```

表示组件获得焦点。

**起始版本：** 23

<!--Device-AccessibilityAction-FOCUS = 2--><!--Device-AccessibilityAction-FOCUS = 2-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## CLEAR_FOCUS

```TypeScript
CLEAR_FOCUS = 3
```

表示清除组件焦点。

**起始版本：** 23

<!--Device-AccessibilityAction-CLEAR_FOCUS = 3--><!--Device-AccessibilityAction-CLEAR_FOCUS = 3-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## CLICK

```TypeScript
CLICK = 4
```

表示点击组件。

**起始版本：** 23

<!--Device-AccessibilityAction-CLICK = 4--><!--Device-AccessibilityAction-CLICK = 4-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## LONG_CLICK

```TypeScript
LONG_CLICK = 5
```

表示长按组件。

**起始版本：** 23

<!--Device-AccessibilityAction-LONG_CLICK = 5--><!--Device-AccessibilityAction-LONG_CLICK = 5-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## CUT

```TypeScript
CUT = 6
```

表示剪切组件内容。

**起始版本：** 23

<!--Device-AccessibilityAction-CUT = 6--><!--Device-AccessibilityAction-CUT = 6-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## COPY

```TypeScript
COPY = 7
```

表示拷贝组件内容。

**起始版本：** 23

<!--Device-AccessibilityAction-COPY = 7--><!--Device-AccessibilityAction-COPY = 7-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## PASTE

```TypeScript
PASTE = 8
```

表示粘贴内容到组件。

**起始版本：** 23

<!--Device-AccessibilityAction-PASTE = 8--><!--Device-AccessibilityAction-PASTE = 8-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SELECT

```TypeScript
SELECT = 9
```

表示选择组件。

**起始版本：** 23

<!--Device-AccessibilityAction-SELECT = 9--><!--Device-AccessibilityAction-SELECT = 9-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SET_TEXT

```TypeScript
SET_TEXT = 10
```

表示设置组件的文本。需配置参数[Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).setText，参数值为要设置的文本内容。

**起始版本：** 23

<!--Device-AccessibilityAction-SET_TEXT = 10--><!--Device-AccessibilityAction-SET_TEXT = 10-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SCROLL_FORWARD

```TypeScript
SCROLL_FORWARD = 11
```

表示向前滚动组件（向内容末尾方向滚动）。需配置参数[Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).scrollType，参数值为' fullScreen'或'halfScreen'。

**起始版本：** 23

<!--Device-AccessibilityAction-SCROLL_FORWARD = 11--><!--Device-AccessibilityAction-SCROLL_FORWARD = 11-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SCROLL_BACKWARD

```TypeScript
SCROLL_BACKWARD = 12
```

表示向后滚动组件（向内容起始方向滚动）。需配置参数[Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).scrollType，参数值为' fullScreen'或'halfScreen'。

**起始版本：** 23

<!--Device-AccessibilityAction-SCROLL_BACKWARD = 12--><!--Device-AccessibilityAction-SCROLL_BACKWARD = 12-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SET_SELECTION

```TypeScript
SET_SELECTION = 13
```

表示选定组件内文本范围。需配置参数[Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).selectTextBegin、 [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).selectTextEnd、 [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).selectTextInForWard，参数值为选定文本的起始坐标、结束坐标及是否向 前选择。

**起始版本：** 23

<!--Device-AccessibilityAction-SET_SELECTION = 13--><!--Device-AccessibilityAction-SET_SELECTION = 13-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SET_CURSOR_POSITION

```TypeScript
SET_CURSOR_POSITION = 14
```

表示设置组件内的光标位置。需配置参数[Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).offset，参数值为光标的字符偏移量。

**起始版本：** 23

<!--Device-AccessibilityAction-SET_CURSOR_POSITION = 14--><!--Device-AccessibilityAction-SET_CURSOR_POSITION = 14-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## HOME

```TypeScript
HOME = 15
```

表示执行返回首页操作。 **使用约束：** 此操作在多屏场景下，仅在主屏幕上生效。

**起始版本：** 23

<!--Device-AccessibilityAction-HOME = 15--><!--Device-AccessibilityAction-HOME = 15-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## BACK

```TypeScript
BACK = 16
```

表示执行返回操作。

**起始版本：** 23

<!--Device-AccessibilityAction-BACK = 16--><!--Device-AccessibilityAction-BACK = 16-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## RECENT_TASK

```TypeScript
RECENT_TASK = 17
```

表示显示最近任务。

**起始版本：** 23

<!--Device-AccessibilityAction-RECENT_TASK = 17--><!--Device-AccessibilityAction-RECENT_TASK = 17-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## NOTIFICATION_CENTER

```TypeScript
NOTIFICATION_CENTER = 18
```

表示显示通知中心。

**起始版本：** 23

<!--Device-AccessibilityAction-NOTIFICATION_CENTER = 18--><!--Device-AccessibilityAction-NOTIFICATION_CENTER = 18-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## CONTROL_CENTER

```TypeScript
CONTROL_CENTER = 19
```

表示显示控制中心。

**起始版本：** 23

<!--Device-AccessibilityAction-CONTROL_CENTER = 19--><!--Device-AccessibilityAction-CONTROL_CENTER = 19-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SPAN_CLICK

```TypeScript
SPAN_CLICK = 20
```

表示对局部文本进行点击操作。需配置参数[Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).spanId，参数值为超链接文本编号。

**起始版本：** 23

<!--Device-AccessibilityAction-SPAN_CLICK = 20--><!--Device-AccessibilityAction-SPAN_CLICK = 20-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## INJECT_ACTION

```TypeScript
INJECT_ACTION = 21
```

表示注入模拟用户操作的动作。需配置参数[Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).injectActionType，参数值为注入 动作类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityAction-INJECT_ACTION = 21--><!--Device-AccessibilityAction-INJECT_ACTION = 21-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## EXECUTE_CUSTOM_ACTION

```TypeScript
EXECUTE_CUSTOM_ACTION = 22
```

表示执行自定义操作。需配置参数[Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md).customAction，参数值为自定义操作的名称。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityAction-EXECUTE_CUSTOM_ACTION = 22--><!--Device-AccessibilityAction-EXECUTE_CUSTOM_ACTION = 22-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

