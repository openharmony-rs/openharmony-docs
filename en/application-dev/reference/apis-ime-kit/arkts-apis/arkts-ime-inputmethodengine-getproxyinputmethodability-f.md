# getProxyInputMethodAbility

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## getProxyInputMethodAbility

```TypeScript
function getProxyInputMethodAbility(): ProxyInputMethodAbility | null
```

Obtains a [ProxyInputMethodAbility](arkts-ime-inputmethodengine-proxyinputmethodability-i.md) instance. The caller must not be an input method extension; <br> <br>The caller as the proxy input method can use the obtained instance to subscribe to a input start event, and more.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-inputMethodEngine-function getProxyInputMethodAbility(): ProxyInputMethodAbility | null--><!--Device-inputMethodEngine-function getProxyInputMethodAbility(): ProxyInputMethodAbility | null-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [ProxyInputMethodAbility](arkts-ime-inputmethodengine-proxyinputmethodability-i.md) &#124; null | **ProxyInputMethodAbility** instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 12800028 | The caller is an input method extension. |
