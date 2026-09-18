# KeyboardDelegate

In the following API examples, you must first use [getKeyboardDelegate](arkts-ime-inputmethodengine-getkeyboarddelegate-f.md) to obtain a **KeyboardDelegate** instance, and then call the APIs using the obtained instance.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## off('keyDown' | 'keyUp')

```TypeScript
off(type: 'keyDown' | 'keyUp', callback?: (event: KeyEvent) => boolean): void
```

Disables listening for a physical keyboard event. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyDown' &#124; 'keyUp' | Yes | Event type.<br>- The value **'keyDown'** indicates the keydown event. <br>- The value **'keyUp'** indicates the keyup event. |
| callback | (event: KeyEvent) =&gt; boolean | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('keyDown' | 'keyUp')

```TypeScript
off(type: 'keyDown' | 'keyUp', callback?: (event: KeyEvent) => boolean): void
```

Disables listening for a physical keyboard event. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyDown' &#124; 'keyUp' | Yes | Event type.<br>- The value **'keyDown'** indicates the keydown event. <br>- The value **'keyUp'** indicates the keyup event. |
| callback | (event: KeyEvent) =&gt; boolean | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('keyEvent')

```TypeScript
off(type: 'keyEvent', callback?: (event: InputKeyEvent) => boolean): void
```

Disables listening for a keyboard event. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyEvent' | Yes | Event type, which is **'keyEvent'**. |
| callback | (event: InputKeyEvent) =&gt; boolean | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('cursorContextChange')

```TypeScript
off(type: 'cursorContextChange', callback?: (x: number, y: number, height: number) => void): void
```

Disables listening for cursor context changes. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'cursorContextChange' | Yes | Event type, which is **'cursorContextChange'**. |
| callback | (x: number, y: number, height: number) =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('selectionChange')

```TypeScript
off(
      type: 'selectionChange',
      callback?: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void
    ): void
```

Disables listening for the text selection change event. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'selectionChange' | Yes | Event type, which is **'selectionChange'**. |
| callback | (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('textChange')

```TypeScript
off(type: 'textChange', callback?: (text: string) => void): void
```

Disables listening for the text change event. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'textChange' | Yes | Event type, which is **'textChange'**. |
| callback | (text: string) =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('editorAttributeChanged')

```TypeScript
off(type: 'editorAttributeChanged', callback?: (attr: EditorAttribute) => void): void
```

Disables listening for the edit box attribute change event. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'editorAttributeChanged' | Yes | Event type, which is **'editorAttributeChanged'**. |
| callback | (attr: EditorAttribute) =&gt; void | No | Callback used for unsubscription. If this parameter is not specified, this API unregisters all callbacks for the specified type by default. |

## on('keyDown' | 'keyUp')

```TypeScript
on(type: 'keyDown' | 'keyUp', callback: (event: KeyEvent) => boolean): void
```

Enables listening for a physical keyboard event. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyDown' &#124; 'keyUp' | Yes | Event type.<br>- The value **'keyDown'** indicates the keydown event. <br>- The value **'keyUp'** indicates the keyup event. |
| callback | (event: KeyEvent) =&gt; boolean | Yes | Callback used to return the key information. If the event is consumed by the event subscriber, **true** is returned. Otherwise, **false** is returned. |

## on('keyDown' | 'keyUp')

```TypeScript
on(type: 'keyDown' | 'keyUp', callback: (event: KeyEvent) => boolean): void
```

Enables listening for a physical keyboard event. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyDown' &#124; 'keyUp' | Yes | Event type.<br>- The value **'keyDown'** indicates the keydown event. <br>- The value **'keyUp'** indicates the keyup event. |
| callback | (event: KeyEvent) =&gt; boolean | Yes | Callback used to return the key information. If the event is consumed by the event subscriber, **true** is returned. Otherwise, **false** is returned. |

## on('keyEvent')

```TypeScript
on(type: 'keyEvent', callback: (event: InputKeyEvent) => boolean): void
```

Enables listening for a keyboard event. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyEvent' | Yes | Event type, which is **'keyEvent'**. |
| callback | (event: InputKeyEvent) =&gt; boolean | Yes | Callback used to return the result. The input parameter is the key event information and the return value is of the Boolean type. <br>- Input parameter: [InputKeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md). <br>- If the event is consumed by the event subscriber, **true** is returned. Otherwise, **false** is returned. |

## on('cursorContextChange')

```TypeScript
on(type: 'cursorContextChange', callback: (x: number, y: number, height: number) => void): void
```

Enables listening for the cursor change event. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'cursorContextChange' | Yes | Event type, which is **'cursorContextChange'**. |
| callback | (x: number, y: number, height: number) =&gt; void | Yes | Callback used to return the cursor information.<br>- **x**: x coordinate of the top of the cursor. <br>- **y**: y coordinate of the bottom of the cursor. <br>- **height**: height of the cursor. |

## on('selectionChange')

```TypeScript
on(
      type: 'selectionChange',
      callback: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void
    ): void
```

Enables listening for the text selection change event. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'selectionChange' | Yes | Event type, which is **'selectionChange'**. |
| callback | (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) =&gt; void | Yes | Callback used to return the text selection information.<br>- **oldBegin**: start of the selected text before the change. <br>- **oldEnd**: end of the selected text before the change. <br>- **newBegin**: start of the selected text after the change. <br>- **newEnd**: end of the selected text after the change. |

## on('textChange')

```TypeScript
on(type: 'textChange', callback: (text: string) => void): void
```

Enables listening for the text change event. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'textChange' | Yes | Event type, which is **'textChange'**. |
| callback | (text: string) =&gt; void | Yes | Callback used to return the text content. |

## on('editorAttributeChanged')

```TypeScript
on(type: 'editorAttributeChanged', callback: (attr: EditorAttribute) => void): void
```

Enables listening for the edit box attribute change event. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'editorAttributeChanged' | Yes | Event type, which is **'editorAttributeChanged'**. |
| callback | (attr: EditorAttribute) =&gt; void | Yes | Callback used to return the changed edit box attribute. |
