# unregisterInAppProxyIme

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## unregisterInAppProxyIme

```TypeScript
function unregisterInAppProxyIme(): Promise<void>
```

Unregisters the proxy input method registered by [registerInAppProxyIme](arkts-ime-inputmethodengine-registerinappproxyime-f.md). This API is idempotent: it returns success even if no proxy is registered.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-inputMethodEngine-function unregisterInAppProxyIme(): Promise<void>--><!--Device-inputMethodEngine-function unregisterInAppProxyIme(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
