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

<!--Device-inputMethod-function setSimpleKeyboardEnabled(enable: boolean): void--><!--Device-inputMethod-function setSimpleKeyboardEnabled(enable: boolean): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Flag indicating whether the simple keyboard is enabled. The value **true** indicates that the simple keyboard is enabled, and **false** indicates that it is disabled.<br> For a native text box component, this takes effect the next time the component is clicked to gain focus. For a custom-drawn control, this takes effect the next time [attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach-1) is called to bind the input method. |

**Examples**

```TypeScript
let enable: boolean = false;
  inputMethod.setSimpleKeyboardEnabled(enable);
```
