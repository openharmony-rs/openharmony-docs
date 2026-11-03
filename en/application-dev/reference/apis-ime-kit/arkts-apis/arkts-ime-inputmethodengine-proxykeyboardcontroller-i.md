# ProxyKeyboardController

```TypeScript
interface ProxyKeyboardController
```

You must first use [onInputStart](arkts-ime-inputmethodengine-proxyinputmethodability-i.md#oninputstart) to obtain a **ProxyKeyboardController** instance, and then use this instance to call the following APIs.

**Since:** 26.1.0

<!--Device-inputMethodEngine-interface ProxyKeyboardController--><!--Device-inputMethodEngine-interface ProxyKeyboardController-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## hideSelf

```TypeScript
hideSelf(): Promise<void>
```

Notifies the framework that the custom keyboard has been hidden. When the user taps the hide button on the custom keyboard, the application calls this API to notify the edit box that the custom keyboard is hidden.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyKeyboardController-hideSelf(): Promise<void>--><!--Device-ProxyKeyboardController-hideSelf(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |
