# WindowFocusState

```TypeScript
interface WindowFocusState
```

描述窗口的焦点状态变化信息。

**起始版本：** 26.0.1

<!--Device-window-interface WindowFocusState--><!--Device-window-interface WindowFocusState-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## focusChangeReason

```TypeScript
focusChangeReason: FocusChangeReason
```

焦点状态变化的原因。

**类型：** [FocusChangeReason](arkts-arkui-window-focuschangereason-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowFocusState-focusChangeReason: FocusChangeReason--><!--Device-WindowFocusState-focusChangeReason: FocusChangeReason-End-->

**系统能力：** SystemCapability.Window.SessionManager

## isFocused

```TypeScript
isFocused: boolean
```

窗口是否获焦。窗口获焦时为true，否则为false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowFocusState-isFocused: boolean--><!--Device-WindowFocusState-isFocused: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## nextFocusedWindowId

```TypeScript
nextFocusedWindowId?: number
```

下一个获焦窗口的ID。该字段仅在窗口失焦、且下一个获焦窗口与本窗口在同一进程时有效。默认值为undefined。该值应为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowFocusState-nextFocusedWindowId?: int--><!--Device-WindowFocusState-nextFocusedWindowId?: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

## prevFocusedWindowId

```TypeScript
prevFocusedWindowId?: number
```

上一个获焦窗口的ID。该字段仅在窗口获焦、且上一个获焦窗口与本窗口在同一进程时有效。默认值为undefined。该值应为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowFocusState-prevFocusedWindowId?: int--><!--Device-WindowFocusState-prevFocusedWindowId?: int-End-->

**系统能力：** SystemCapability.Window.SessionManager
