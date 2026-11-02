# getProxyKeyboardDelegate

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## getProxyKeyboardDelegate

```TypeScript
function getProxyKeyboardDelegate(): ProxyKeyboardDelegate | null
```

Obtains a [ProxyKeyboardDelegate](arkts-ime-inputmethodengine-proxykeyboarddelegate-i.md) instance. The caller must not be an input method extension; <br> <br>The caller as the proxy input method can use the instance to subscribe to a physical keyboard event, text selection change event, and more.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-inputMethodEngine-function getProxyKeyboardDelegate(): ProxyKeyboardDelegate | null--><!--Device-inputMethodEngine-function getProxyKeyboardDelegate(): ProxyKeyboardDelegate | null-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [ProxyKeyboardDelegate](arkts-ime-inputmethodengine-proxykeyboarddelegate-i.md) &#124; null | **ProxyKeyboardDelegate** instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 12800028 | The caller is an input method extension. |
