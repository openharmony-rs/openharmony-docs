# HotkeyOptions

Defines shortcut key options.

**Since:** 14

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

## Modules to Import

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## finalKey

```TypeScript
finalKey: number
```

Modified key, which can be any key except the modifier keys and Meta key. For details about the keys, see [@ohos.multimodalInput.keyCode (Keycode)](arkts-input-multimodalinput-keycode-keycode-e.md).

For example, in **Ctrl+Shift+Esc**, **Esc** is the modifier key.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

## isRepeat

```TypeScript
isRepeat?: boolean
```

Whether to report repeated key events. The value **true** means to report repeated key events, and the value **false** means the opposite. The default value is **true**.

**Type:** boolean

**Since:** 14

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

## preKeys

```TypeScript
preKeys: Array<number>
```

Modifier key set (including Ctrl, Shift, and Alt). One to four modifier keys are supported. There is no requirement on the sequence of modifier keys.

For example, in **Ctrl+Shift+Esc**, **Ctrl** and **Shift** are modifier keys.

**Type:** Array&lt;number&gt;

**Since:** 14

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer
