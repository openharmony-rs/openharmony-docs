# KeyEvent（系统接口）

按键注入描述信息。

**起始版本：** 8

<!--Device-inputEventClient-interface KeyEvent--><!--Device-inputEventClient-interface KeyEvent-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## isIntercepted

```TypeScript
isIntercepted: boolean
```

按键是否可以被拦截。

true表示可以被拦截，false表示不可被拦截。

**类型：** boolean

**起始版本：** 8

<!--Device-KeyEvent-isIntercepted: boolean--><!--Device-KeyEvent-isIntercepted: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

## isPressed

```TypeScript
isPressed: boolean
```

按键是否按下。

true表示按键按下，false表示按键抬起。

**类型：** boolean

**起始版本：** 8

<!--Device-KeyEvent-isPressed: boolean--><!--Device-KeyEvent-isPressed: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

## keyCode

```TypeScript
keyCode: number
```

按键键值。当前仅支持返回键/KEYCODE_BACK键。

**类型：** number

**起始版本：** 8

<!--Device-KeyEvent-keyCode: int--><!--Device-KeyEvent-keyCode: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

## keyDownDuration

```TypeScript
keyDownDuration: number
```

按键按下持续时间，单位为微秒（μs）。

**类型：** number

**起始版本：** 8

<!--Device-KeyEvent-keyDownDuration: int--><!--Device-KeyEvent-keyDownDuration: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

