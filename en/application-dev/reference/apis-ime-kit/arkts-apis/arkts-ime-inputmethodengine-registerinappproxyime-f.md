# registerInAppProxyIme

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## registerInAppProxyIme

```TypeScript
function registerInAppProxyIme(options?: RegisterOptions): Promise<void>
```

Registers a proxy input method. The proxy input method is activated when an edit box in the same process gains focus, triggers input method binding, and matches the options specified in **RegisterOptions**.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-inputMethodEngine-function registerInAppProxyIme(options?: RegisterOptions): Promise<void>--><!--Device-inputMethodEngine-function registerInAppProxyIme(options?: RegisterOptions): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RegisterOptions](arkts-ime-inputmethodengine-registeroptions-i.md) | No | Options for registering the proxy input method. If not specified, all edit box patterns are proxied. If called again with different options, the new options take effect (last wins). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 12800027 | The caller is not a focused application. |
| 12800028 | The caller is an input method extension. |
