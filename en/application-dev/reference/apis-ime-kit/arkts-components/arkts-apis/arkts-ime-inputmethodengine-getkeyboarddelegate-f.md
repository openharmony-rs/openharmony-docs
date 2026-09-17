# getKeyboardDelegate

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## getKeyboardDelegate

```TypeScript
function getKeyboardDelegate(): KeyboardDelegate
```

Obtains a [KeyboardDelegate](arkts-ime-inputmethodengine-keyboarddelegate-i.md) instance for the input method. <br> <br>The input method can use the obtained instance to subscribe to a physical keyboard event, text selection change event, and more.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [KeyboardDelegate](arkts-ime-inputmethodengine-keyboarddelegate-i.md) | **KeyboardDelegate** instance. |

**Examples**

```TypeScript
let KeyboardDelegate: inputMethodEngine.KeyboardDelegate = inputMethodEngine.getKeyboardDelegate();
```
