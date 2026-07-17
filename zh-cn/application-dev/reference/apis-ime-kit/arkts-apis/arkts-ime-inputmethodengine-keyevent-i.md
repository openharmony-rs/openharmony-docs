# KeyEvent

按键属性值。

**起始版本：** 8

<!--Device-inputMethodEngine-interface KeyEvent--><!--Device-inputMethodEngine-interface KeyEvent-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## keyAction

```TypeScript
readonly keyAction: number
```

按键事件类型。

- 当值为2时，表示按下事件；  
- 当值为3时，表示抬起事件。

**类型：** number

**起始版本：** 8

<!--Device-KeyEvent-readonly keyAction: int--><!--Device-KeyEvent-readonly keyAction: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## keyCode

```TypeScript
readonly keyCode: number
```

按键的键值。键码值说明参考[KeyCode](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keycode-keycode-e.md)。

**类型：** number

**起始版本：** 8

<!--Device-KeyEvent-readonly keyCode: int--><!--Device-KeyEvent-readonly keyCode: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

