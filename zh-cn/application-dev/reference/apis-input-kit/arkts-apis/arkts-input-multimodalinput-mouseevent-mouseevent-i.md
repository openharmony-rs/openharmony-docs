# MouseEvent

鼠标事件。

**继承/实现关系：** MouseEvent extends [InputEvent](arkts-input-multimodalinput-inputevent-inputevent-i.md)

**起始版本：** 9

<!--Device-unnamed-export declare interface MouseEvent extends InputEvent--><!--Device-unnamed-export declare interface MouseEvent extends InputEvent-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## 导入模块

```TypeScript
import { MouseAction, AxisValue, MouseEvent, Button, MouseToolType, Axis } from '@kit.InputKit';
```

## action

```TypeScript
action: Action
```

鼠标事件类型。

**类型：** Action

**起始版本：** 9

<!--Device-MouseEvent-action: Action--><!--Device-MouseEvent-action: Action-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## altKey

```TypeScript
altKey: boolean
```

当前altKey是否处于按下状态。

true表示处于按下状态，false表示处于抬起状态。

**类型：** boolean

**起始版本：** 9

<!--Device-MouseEvent-altKey: boolean--><!--Device-MouseEvent-altKey: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## axes

```TypeScript
axes: AxisValue[]
```

鼠标轴类型和轴的值。

**类型：** AxisValue[]

**起始版本：** 9

<!--Device-MouseEvent-axes: AxisValue[]--><!--Device-MouseEvent-axes: AxisValue[]-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## button

```TypeScript
button: Button
```

鼠标按键。

**类型：** Button

**起始版本：** 9

<!--Device-MouseEvent-button: Button--><!--Device-MouseEvent-button: Button-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## capsLock

```TypeScript
capsLock: boolean
```

当前capsLock是否处于使能状态。

true表示使能状态，false表示处于未使能状态。

**类型：** boolean

**起始版本：** 9

<!--Device-MouseEvent-capsLock: boolean--><!--Device-MouseEvent-capsLock: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## ctrlKey

```TypeScript
ctrlKey: boolean
```

当前ctrlKey是否处于按下状态。

true表示处于按下状态，false表示处于抬起状态。

**类型：** boolean

**起始版本：** 9

<!--Device-MouseEvent-ctrlKey: boolean--><!--Device-MouseEvent-ctrlKey: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## fnKey

```TypeScript
fnKey: boolean
```

当前fnKey是否处于按下状态。

true表示处于按下状态，false表示处于抬起状态。

**类型：** boolean

**起始版本：** 9

<!--Device-MouseEvent-fnKey: boolean--><!--Device-MouseEvent-fnKey: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## globalX

```TypeScript
globalX?: number
```

该鼠标事件以主屏左上角为原点的全局坐标系的X坐标，单位为像素（px）。<!--Del-->作为入参时，若接口参数中的[MouseEventData.useGlobalCoordinate](arkts-input-inputeventclient-mouseeventdata-i-sys.md)为true，该值必填，当前仅支持整数。若为false，该值无需填写，使用指定屏幕左上角为原点的相对坐标系的X坐标计算注入事件。<!--DelEnd-->作为出参时，由系统上报。

**类型：** number

**起始版本：** 20

<!--Device-MouseEvent-globalX?: int--><!--Device-MouseEvent-globalX?: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## globalY

```TypeScript
globalY?: number
```

该鼠标事件以主屏左上角为原点的全局坐标系的Y坐标，单位为像素（px）。<!--Del-->作为入参时，若接口参数中的[MouseEventData.useGlobalCoordinate](arkts-input-inputeventclient-mouseeventdata-i-sys.md)为true，该值必填，当前仅支持整数。若为false，该值无需填写，使用指定屏幕左上角为原点的相对坐标系的Y坐标计算注入事件。<!--DelEnd-->作为出参时，由系统上报。

**类型：** number

**起始版本：** 20

<!--Device-MouseEvent-globalY?: int--><!--Device-MouseEvent-globalY?: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## logoKey

```TypeScript
logoKey: boolean
```

当前logoKey是否处于按下状态。

true表示处于按下状态，false表示处于抬起状态。

**类型：** boolean

**起始版本：** 9

<!--Device-MouseEvent-logoKey: boolean--><!--Device-MouseEvent-logoKey: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## numLock

```TypeScript
numLock: boolean
```

当前numLock是否处于使能状态。

true表示使能状态，false表示处于未使能状态。

**类型：** boolean

**起始版本：** 9

<!--Device-MouseEvent-numLock: boolean--><!--Device-MouseEvent-numLock: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## pressedButtons

```TypeScript
pressedButtons: Button[]
```

当前处于按下状态的鼠标按键。

**类型：** Button[]

**起始版本：** 9

<!--Device-MouseEvent-pressedButtons: Button[]--><!--Device-MouseEvent-pressedButtons: Button[]-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## pressedKeys

```TypeScript
pressedKeys: KeyCode[]
```

当前处于按下状态的键值列表。

**类型：** KeyCode[]

**起始版本：** 9

<!--Device-MouseEvent-pressedKeys: KeyCode[]--><!--Device-MouseEvent-pressedKeys: KeyCode[]-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## rawDeltaX

```TypeScript
rawDeltaX: number
```

鼠标当前事件相对于上次事件的X坐标偏移值。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

<!--Device-MouseEvent-rawDeltaX: int--><!--Device-MouseEvent-rawDeltaX: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## rawDeltaY

```TypeScript
rawDeltaY: number
```

鼠标当前事件相对于上次事件的Y坐标偏移值。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

<!--Device-MouseEvent-rawDeltaY: int--><!--Device-MouseEvent-rawDeltaY: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## screenX

```TypeScript
screenX: number
```

该鼠标事件以指定屏幕左上角为原点的相对坐标系的X坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

<!--Device-MouseEvent-screenX: int--><!--Device-MouseEvent-screenX: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## screenY

```TypeScript
screenY: number
```

该鼠标事件以指定屏幕左上角为原点的相对坐标系的Y坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

<!--Device-MouseEvent-screenY: int--><!--Device-MouseEvent-screenY: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## scrollLock

```TypeScript
scrollLock: boolean
```

当前scrollLock是否处于使能状态。

true表示使能状态，false表示处于未使能状态。

**类型：** boolean

**起始版本：** 9

<!--Device-MouseEvent-scrollLock: boolean--><!--Device-MouseEvent-scrollLock: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## shiftKey

```TypeScript
shiftKey: boolean
```

当前shiftKey是否处于按下状态。

true表示处于按下状态，false表示处于抬起状态。

**类型：** boolean

**起始版本：** 9

<!--Device-MouseEvent-shiftKey: boolean--><!--Device-MouseEvent-shiftKey: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## toolType

```TypeScript
toolType: ToolType
```

工具类型。

**类型：** ToolType

**起始版本：** 11

<!--Device-MouseEvent-toolType: ToolType--><!--Device-MouseEvent-toolType: ToolType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## windowX

```TypeScript
windowX: number
```

鼠标所在窗口左上角为原点的相对坐标系的X坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

<!--Device-MouseEvent-windowX: int--><!--Device-MouseEvent-windowX: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## windowY

```TypeScript
windowY: number
```

鼠标所在窗口左上角为原点的相对坐标系的Y坐标。当前仅支持整数，单位为像素（px）。

**类型：** number

**起始版本：** 9

<!--Device-MouseEvent-windowY: int--><!--Device-MouseEvent-windowY: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

