# ProxyInputMethodAbility

```TypeScript
interface ProxyInputMethodAbility
```

In the following API examples, you must first use [getProxyInputMethodAbility](arkts-ime-inputmethodengine-getproxyinputmethodability-f.md) to obtain a **ProxyInputMethodAbility** instance, and then call the APIs using the obtained instance.

**Since:** 26.1.0

<!--Device-inputMethodEngine-interface ProxyInputMethodAbility--><!--Device-inputMethodEngine-interface ProxyInputMethodAbility-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## offInputStart

```TypeScript
offInputStart(callback?: ProxyInputStartCallback): void
```

Unsubscribe 'inputStart' event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyInputMethodAbility-offInputStart(callback?: ProxyInputStartCallback): void--><!--Device-ProxyInputMethodAbility-offInputStart(callback?: ProxyInputStartCallback): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ProxyInputStartCallback](arkts-ime-inputmethodengine-proxyinputstartcallback-t.md) | No | optional, the callback called when an edit box requests the proxy input method. |

## offKeyboardHide

```TypeScript
offKeyboardHide(callback?: Callback<void>): void
```

Unsubscribe 'keyboardHide' event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyInputMethodAbility-offKeyboardHide(callback?: Callback<void>): void--><!--Device-ProxyInputMethodAbility-offKeyboardHide(callback?: Callback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | optional, the callback called when the proxy keyboard should be hidden. |

## offKeyboardShow

```TypeScript
offKeyboardShow(callback?: Callback<void>): void
```

Unsubscribe 'keyboardShow' event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyInputMethodAbility-offKeyboardShow(callback?: Callback<void>): void--><!--Device-ProxyInputMethodAbility-offKeyboardShow(callback?: Callback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | optional, the callback called when the proxy keyboard should be shown. |

## offUnregister

```TypeScript
offUnregister(callback?: Callback<void>): void
```

Unsubscribe 'unregister' event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyInputMethodAbility-offUnregister(callback?: Callback<void>): void--><!--Device-ProxyInputMethodAbility-offUnregister(callback?: Callback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | optional, the callback called when the proxy input method is passively unregistered. |

## onInputStart

```TypeScript
onInputStart(callback: ProxyInputStartCallback): void
```

Subscribe 'inputStart' event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyInputMethodAbility-onInputStart(callback: ProxyInputStartCallback): void--><!--Device-ProxyInputMethodAbility-onInputStart(callback: ProxyInputStartCallback): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ProxyInputStartCallback](arkts-ime-inputmethodengine-proxyinputstartcallback-t.md) | Yes | the callback called when an edit box requests the proxy input method. |

## onKeyboardHide

```TypeScript
onKeyboardHide(callback: Callback<void>): void
```

Subscribe 'keyboardHide' event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyInputMethodAbility-onKeyboardHide(callback: Callback<void>): void--><!--Device-ProxyInputMethodAbility-onKeyboardHide(callback: Callback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | the callback called when the proxy keyboard should be hidden. |

## onKeyboardShow

```TypeScript
onKeyboardShow(callback: Callback<void>): void
```

Subscribe 'keyboardShow' event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyInputMethodAbility-onKeyboardShow(callback: Callback<void>): void--><!--Device-ProxyInputMethodAbility-onKeyboardShow(callback: Callback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | the callback called when the proxy keyboard should be shown. |

## onUnregister

```TypeScript
onUnregister(callback: Callback<void>): void
```

Subscribe 'unregister' event. This event is triggered when the framework passively unregisters the proxy input method (e.g., when the registration limit is exceeded). After receiving this callback, if the app is currently focused and needs to continue using the proxy input method, it should call registerInAppProxyIme again immediately; if not focused, it should re-register when it regains focus.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyInputMethodAbility-onUnregister(callback: Callback<void>): void--><!--Device-ProxyInputMethodAbility-onUnregister(callback: Callback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | the callback called when the proxy input method is passively unregistered. |
