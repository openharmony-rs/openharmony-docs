# ProxyKeyboardDelegate

```TypeScript
interface ProxyKeyboardDelegate
```

In the following API examples, you must first use [getProxyKeyboardDelegate](arkts-ime-inputmethodengine-getproxykeyboarddelegate-f.md) to obtain a **ProxyKeyboardDelegate** instance, and then call the APIs using the obtained instance.

**Since:** 26.1.0

<!--Device-inputMethodEngine-interface ProxyKeyboardDelegate--><!--Device-inputMethodEngine-interface ProxyKeyboardDelegate-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## offCursorContextChange

```TypeScript
offCursorContextChange(callback?: CursorContextChangeCallback): void
```

Unsubscribe cursor context change.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyKeyboardDelegate-offCursorContextChange(callback?: CursorContextChangeCallback): void--><!--Device-ProxyKeyboardDelegate-offCursorContextChange(callback?: CursorContextChangeCallback): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | CursorContextChangeCallback | No | optional, the callback called when cursor information changes. |

## offEditorAttributeChanged

```TypeScript
offEditorAttributeChanged(callback?: Callback<EditorAttribute>): void
```

Unsubscribe input text attribute change.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyKeyboardDelegate-offEditorAttributeChanged(callback?: Callback<EditorAttribute>): void--><!--Device-ProxyKeyboardDelegate-offEditorAttributeChanged(callback?: Callback<EditorAttribute>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[EditorAttribute](arkts-ime-inputmethodengine-editorattribute-i.md)&gt; | No | optional, the callback called when editor's attribute changes. |

## offKeyEvent

```TypeScript
offKeyEvent(callback?: InputKeyEventCallback): void
```

Unsubscribe key event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyKeyboardDelegate-offKeyEvent(callback?: InputKeyEventCallback): void--><!--Device-ProxyKeyboardDelegate-offKeyEvent(callback?: InputKeyEventCallback): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | InputKeyEventCallback | No | optional, the callback called when a key event occurs. |

## offSelectionChange

```TypeScript
offSelectionChange(callback?: SelectionChangeCallback): void
```

Unsubscribe selection change.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyKeyboardDelegate-offSelectionChange(callback?: SelectionChangeCallback): void--><!--Device-ProxyKeyboardDelegate-offSelectionChange(callback?: SelectionChangeCallback): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | SelectionChangeCallback | No | optional, the callback called when the text selection changes. |

## offTextChange

```TypeScript
offTextChange(callback?: Callback<string>): void
```

Unsubscribe text change.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyKeyboardDelegate-offTextChange(callback?: Callback<string>): void--><!--Device-ProxyKeyboardDelegate-offTextChange(callback?: Callback<string>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | No | optional, the callback called when the text changes. |

## onCursorContextChange

```TypeScript
onCursorContextChange(callback: CursorContextChangeCallback): void
```

Subscribe cursor context change.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyKeyboardDelegate-onCursorContextChange(callback: CursorContextChangeCallback): void--><!--Device-ProxyKeyboardDelegate-onCursorContextChange(callback: CursorContextChangeCallback): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | CursorContextChangeCallback | Yes | the callback called when cursor information changes. |

## onEditorAttributeChanged

```TypeScript
onEditorAttributeChanged(callback: Callback<EditorAttribute>): void
```

Subscribe input text attribute change.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyKeyboardDelegate-onEditorAttributeChanged(callback: Callback<EditorAttribute>): void--><!--Device-ProxyKeyboardDelegate-onEditorAttributeChanged(callback: Callback<EditorAttribute>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[EditorAttribute](arkts-ime-inputmethodengine-editorattribute-i.md)&gt; | Yes | the callback called when editor's attribute changes. |

## onKeyEvent

```TypeScript
onKeyEvent(callback: InputKeyEventCallback): void
```

Subscribe key event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyKeyboardDelegate-onKeyEvent(callback: InputKeyEventCallback): void--><!--Device-ProxyKeyboardDelegate-onKeyEvent(callback: InputKeyEventCallback): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | InputKeyEventCallback | Yes | the callback called when a key event occurs. If the key is processed by event subscriber, callback should be return true, else return false. |

## onSelectionChange

```TypeScript
onSelectionChange(callback: SelectionChangeCallback): void
```

Subscribe selection change.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyKeyboardDelegate-onSelectionChange(callback: SelectionChangeCallback): void--><!--Device-ProxyKeyboardDelegate-onSelectionChange(callback: SelectionChangeCallback): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | SelectionChangeCallback | Yes | the callback called when the text selection changes. |

## onTextChange

```TypeScript
onTextChange(callback: Callback<string>): void
```

Subscribe text change.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyKeyboardDelegate-onTextChange(callback: Callback<string>): void--><!--Device-ProxyKeyboardDelegate-onTextChange(callback: Callback<string>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | Yes | the callback called when the text changes. |
