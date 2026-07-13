# AccessibilityAction（系统接口）

表示无障碍节点元素可执行的操作枚举。

无障碍节点元素是指，UI界面上可执行无障碍操作的一些组件，例如：按钮、文本输入框等组件。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## ACCESSIBILITY_FOCUS

```TypeScript
ACCESSIBILITY_FOCUS = 0
```

表示获得无障碍焦点。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## CLEAR_ACCESSIBILITY_FOCUS

```TypeScript
CLEAR_ACCESSIBILITY_FOCUS = 1
```

表示清除无障碍焦点。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## FOCUS

```TypeScript
FOCUS = 2
```

表示组件获得焦点。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## CLEAR_FOCUS

```TypeScript
CLEAR_FOCUS = 3
```

表示清除组件焦点。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## CLICK

```TypeScript
CLICK = 4
```

表示点击组件。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## LONG_CLICK

```TypeScript
LONG_CLICK = 5
```

表示长按点击组件。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## CUT

```TypeScript
CUT = 6
```

表示剪切组件内容。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## COPY

```TypeScript
COPY = 7
```

表示拷贝组件内容。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## PASTE

```TypeScript
PASTE = 8
```

表示粘贴内容到组件。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SELECT

```TypeScript
SELECT = 9
```

表示选择组件。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SET_TEXT

```TypeScript
SET_TEXT = 10
```

表示设置组件的文本。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SCROLL_FORWARD

```TypeScript
SCROLL_FORWARD = 11
```

表示向前滚动组件。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SCROLL_BACKWARD

```TypeScript
SCROLL_BACKWARD = 12
```

表示向后滚动组件。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SET_SELECTION

```TypeScript
SET_SELECTION = 13
```

表示选定组件内文本范围。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SET_CURSOR_POSITION

```TypeScript
SET_CURSOR_POSITION = 14
```

表示设置组件内的光标位置。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## HOME

```TypeScript
HOME = 15
```

表示组件返回首页操作。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## BACK

```TypeScript
BACK = 16
```

表示执行返回操作。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## RECENT_TASK

```TypeScript
RECENT_TASK = 17
```

显示最近任务。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## NOTIFICATION_CENTER

```TypeScript
NOTIFICATION_CENTER = 18
```

显示通知中心。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## CONTROL_CENTER

```TypeScript
CONTROL_CENTER = 19
```

显示控制中心。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## SPAN_CLICK

```TypeScript
SPAN_CLICK = 20
```

对局部文本进行点击操作。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## INJECT_ACTION

```TypeScript
INJECT_ACTION = 21
```

表示注入动作。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## EXECUTE_CUSTOM_ACTION

```TypeScript
EXECUTE_CUSTOM_ACTION = 22
```

Execute custom action on a component.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

