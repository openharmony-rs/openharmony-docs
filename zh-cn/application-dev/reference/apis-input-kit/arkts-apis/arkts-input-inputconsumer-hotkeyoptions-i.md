# HotkeyOptions

快捷键选项。

**起始版本：** 14

<!--Device-inputConsumer-interface HotkeyOptions--><!--Device-inputConsumer-interface HotkeyOptions-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

## 导入模块

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## finalKey

```TypeScript
finalKey: number
```

被修饰键，除修饰键和Meta键以外的按键，详细按键介绍请参见[@ohos.multimodalInput.keyCode (键值)](arkts-input-multimodalinput-keycode-keycode-e.md)。

例如，Ctrl+Shift+Esc中，Esc称为被修饰键。

**类型：** number

**起始版本：** 14

<!--Device-HotkeyOptions-finalKey: int--><!--Device-HotkeyOptions-finalKey: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

## isRepeat

```TypeScript
isRepeat?: boolean
```

是否上报重复的按键事件。true表示上报，false表示不上报，默认值为true。

**类型：** boolean

**起始版本：** 14

<!--Device-HotkeyOptions-isRepeat?: boolean--><!--Device-HotkeyOptions-isRepeat?: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

## preKeys

```TypeScript
preKeys: Array<number>
```

修饰键（包括 Ctrl、Shift 和 Alt）集合，数量范围[1, 4]，无顺序要求。

例如，Ctrl+Shift+Esc中，Ctrl+Shift称为修饰键。

**类型：** Array<number>

**起始版本：** 14

<!--Device-HotkeyOptions-preKeys: Array<int>--><!--Device-HotkeyOptions-preKeys: Array<int>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

