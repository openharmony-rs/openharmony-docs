# KeyEvent

按键事件。

**继承/实现关系：** KeyEvent extends [InputEvent](arkts-input-multimodalinput-inputevent-inputevent-i.md)

**起始版本：** 9

<!--Device-unnamed-export declare interface KeyEvent extends InputEvent--><!--Device-unnamed-export declare interface KeyEvent extends InputEvent-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## 导入模块

```TypeScript
import { KeyEvent, Action, Key } from '@kit.InputKit';
```

## action

```TypeScript
action: Action
```

按键事件类型。

**类型：** Action

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-action: Action--><!--Device-KeyEvent-action: Action-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## altKey

```TypeScript
altKey: boolean
```

当前altKey是否处于按下状态。

true表示处于按下状态，false表示处于抬起状态。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-altKey: boolean--><!--Device-KeyEvent-altKey: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## capsLock

```TypeScript
capsLock: boolean
```

当前capsLock是否处于使能状态。

true表示处于使能状态，false表示处于未使能状态。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-capsLock: boolean--><!--Device-KeyEvent-capsLock: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## ctrlKey

```TypeScript
ctrlKey: boolean
```

当前ctrlKey是否处于按下状态。

true表示处于按下状态，false表示处于抬起状态。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-ctrlKey: boolean--><!--Device-KeyEvent-ctrlKey: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## fnKey

```TypeScript
fnKey: boolean
```

当前fnKey是否处于按下状态。

true表示处于按下状态，false表示处于抬起状态。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-fnKey: boolean--><!--Device-KeyEvent-fnKey: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## key

```TypeScript
key: Key
```

按键。

**类型：** Key

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-key: Key--><!--Device-KeyEvent-key: Key-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## keys

```TypeScript
keys: Key[]
```

当前处于按下状态的按键列表。

**类型：** Key[]

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-keys: Key[]--><!--Device-KeyEvent-keys: Key[]-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## logoKey

```TypeScript
logoKey: boolean
```

当前logoKey是否处于按下状态。

true表示处于按下状态，false表示处于抬起状态。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-logoKey: boolean--><!--Device-KeyEvent-logoKey: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## numLock

```TypeScript
numLock: boolean
```

当前numLock是否处于使能状态。

true表示处于使能状态，false表示处于未使能状态。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-numLock: boolean--><!--Device-KeyEvent-numLock: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## scrollLock

```TypeScript
scrollLock: boolean
```

当前scrollLock是否处于使能状态。

true表示处于使能状态，false表示处于未使能状态。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-scrollLock: boolean--><!--Device-KeyEvent-scrollLock: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## shiftKey

```TypeScript
shiftKey: boolean
```

当前shiftKey是否处于按下状态。

true表示处于按下状态，false表示处于抬起状态。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-shiftKey: boolean--><!--Device-KeyEvent-shiftKey: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## unicodeChar

```TypeScript
unicodeChar: number
```

按键对应的unicode字符。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-unicodeChar: int--><!--Device-KeyEvent-unicodeChar: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

