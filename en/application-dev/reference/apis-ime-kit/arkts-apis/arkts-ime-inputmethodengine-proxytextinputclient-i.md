# ProxyTextInputClient

```TypeScript
interface ProxyTextInputClient
```

In the following API examples, you must first use [onInputStart](arkts-ime-inputmethodengine-proxyinputmethodability-i.md#oninputstart) to obtain a **ProxyTextInputClient** instance, and then call the APIs using the obtained instance.

**Since:** 26.1.0

<!--Device-inputMethodEngine-interface ProxyTextInputClient--><!--Device-inputMethodEngine-interface ProxyTextInputClient-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## deleteBackward

```TypeScript
deleteBackward(length: number): Promise<void>
```

Deletes the fixed-length text after the cursor. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-deleteBackward(length: int): Promise<void>--><!--Device-ProxyTextInputClient-deleteBackward(length: int): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes | Text length, which cannot be less than 0. <br> The vale should be an integer |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |
| [12800016](../errorcode-inputmethod-framework.md#12800016-input-method-client-not-in-edit-mode) | input method client is not editable. |

## deleteForward

```TypeScript
deleteForward(length: number): Promise<void>
```

Deletes the fixed-length text before the cursor. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-deleteForward(length: int): Promise<void>--><!--Device-ProxyTextInputClient-deleteForward(length: int): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes | Text length, which cannot be less than 0. <br> The vale should be an integer |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |
| [12800016](../errorcode-inputmethod-framework.md#12800016-input-method-client-not-in-edit-mode) | input method client is not editable. |

## getBackward

```TypeScript
getBackward(length: number): Promise<string>
```

Obtains the specific-length text after the cursor. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-getBackward(length: int): Promise<string>--><!--Device-ProxyTextInputClient-getBackward(length: int): Promise<string>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes | Text length, which cannot be less than 0. <br> The vale should be an integer |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the specific-length text after the cursor. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |
| [12800016](../errorcode-inputmethod-framework.md#12800016-input-method-client-not-in-edit-mode) | input method client is not editable. |

## getEditorAttribute

```TypeScript
getEditorAttribute(): Promise<EditorAttribute>
```

Obtains the attribute of the edit box. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-getEditorAttribute(): Promise<EditorAttribute>--><!--Device-ProxyTextInputClient-getEditorAttribute(): Promise<EditorAttribute>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[EditorAttribute](arkts-ime-inputmethodengine-editorattribute-i.md)&gt; | Promise used to return the attribute of the edit box. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |

## getForward

```TypeScript
getForward(length: number): Promise<string>
```

Obtains the specific-length text before the cursor. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-getForward(length: int): Promise<string>--><!--Device-ProxyTextInputClient-getForward(length: int): Promise<string>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes | Text length, which cannot be less than 0. <br> The vale should be an integer |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the specific-length text before the cursor. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |
| [12800016](../errorcode-inputmethod-framework.md#12800016-input-method-client-not-in-edit-mode) | input method client is not editable. |

## getTextIndexAtCursor

```TypeScript
getTextIndexAtCursor(): Promise<number>
```

Obtains the index of the text where the cursor is located. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-getTextIndexAtCursor(): Promise<int>--><!--Device-ProxyTextInputClient-getTextIndexAtCursor(): Promise<int>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |
| [12800016](../errorcode-inputmethod-framework.md#12800016-input-method-client-not-in-edit-mode) | input method client is not editable. |

## insertText

```TypeScript
insertText(text: string): Promise<void>
```

Inserts text. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-insertText(text: string): Promise<void>--><!--Device-ProxyTextInputClient-insertText(text: string): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text to insert. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |
| [12800016](../errorcode-inputmethod-framework.md#12800016-input-method-client-not-in-edit-mode) | input method client is not editable. |

## moveCursor

```TypeScript
moveCursor(direction: Direction): Promise<void>
```

Moves the cursor. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-moveCursor(direction: Direction): Promise<void>--><!--Device-ProxyTextInputClient-moveCursor(direction: Direction): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| direction | [Direction](arkts-ime-inputmethodengine-direction-e.md) | Yes | Direction in which the cursor moves. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |
| [12800016](../errorcode-inputmethod-framework.md#12800016-input-method-client-not-in-edit-mode) | input method client is not editable. |

## selectByMovement

```TypeScript
selectByMovement(movement: Movement): Promise<void>
```

Selects text based on the cursor movement direction. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-selectByMovement(movement: Movement): Promise<void>--><!--Device-ProxyTextInputClient-selectByMovement(movement: Movement): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| movement | [Movement](arkts-ime-inputmethodengine-movement-i.md) | Yes | Direction in which the cursor moves when the text is selected. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |

## selectByRange

```TypeScript
selectByRange(range: Range): Promise<void>
```

Selects text based on the specified range. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-selectByRange(range: Range): Promise<void>--><!--Device-ProxyTextInputClient-selectByRange(range: Range): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [Range](arkts-ime-inputmethodengine-range-i.md) | Yes | Range of the selected text. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |

## sendExtendAction

```TypeScript
sendExtendAction(action: ExtendAction): Promise<void>
```

Sends an extended edit action. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-sendExtendAction(action: ExtendAction): Promise<void>--><!--Device-ProxyTextInputClient-sendExtendAction(action: ExtendAction): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| action | [ExtendAction](arkts-ime-inputmethodengine-extendaction-e.md) | Yes | Extended edit action to send. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |
| [12800016](../errorcode-inputmethod-framework.md#12800016-input-method-client-not-in-edit-mode) | input method client is not editable. |

## sendKeyFunction

```TypeScript
sendKeyFunction(action: number): Promise<void>
```

Sends the function key. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyTextInputClient-sendKeyFunction(action: int): Promise<void>--><!--Device-ProxyTextInputClient-sendKeyFunction(action: int): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| action | number | Yes | Action of the function key. The value **must be** one of the ENTER_KEY_TYPE_* constants, such as [ENTER_KEY_TYPE_UNSPECIFIED](arkts-ime-inputmethodengine-con.md#enter_key_type_unspecified) or [ENTER_KEY_TYPE_DONE](arkts-ime-inputmethodengine-con.md#enter_key_type_done). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to the proxy input method. |
| [12800016](../errorcode-inputmethod-framework.md#12800016-input-method-client-not-in-edit-mode) | input method client is not editable. |
