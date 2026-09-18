# setSimpleKeyboardEnabled

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## setSimpleKeyboardEnabled

```TypeScript
function setSimpleKeyboardEnabled(enable: boolean): void
```

Enables or disables the simple keyboard.

**Since:** 20

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the simple keyboard. The value **true** means that the simple keyboard is enabled; the value **false** means the opposite. <br> The native edit box takes effect when it is focused next time, while the self-drawing component takes effect when the input method is attached by calling [attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach) next time. |

**Examples**

```TypeScript
let enable: boolean = false;
  inputMethod.setSimpleKeyboardEnabled(enable);
```
