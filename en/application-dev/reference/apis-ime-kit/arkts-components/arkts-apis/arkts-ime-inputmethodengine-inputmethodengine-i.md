# InputMethodEngine

In the following API examples, you must first use [getInputMethodEngine](arkts-ime-inputmethodengine-getinputmethodengine-f.md) to obtain an **InputMethodEngine** instance, and then call the APIs using the obtained instance.

**Since:** 8

**Deprecated since:** 23

**Substitutes:** [InputMethodAbility](arkts-ime-inputmethodengine-inputmethodability-i.md)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## off('inputStart')

```TypeScript
off(
      type: 'inputStart',
      callback?: (kbController: KeyboardController, textInputClient: TextInputClient) => void
    ): void
```

Disables listening for the input method binding event.

**Since:** 8

**Deprecated since:** 23

**Substitutes:** [off](arkts-ime-inputmethodengine-inputmethodability-i.md#offinputstart)(type: 'inputStart', callback?: (kbController: KeyboardController, inputClient: InputClient) =&gt; void)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'inputStart' | Yes | Event type, which is **'inputStart'**. |
| callback | (kbController: KeyboardController, textInputClient: TextInputClient) =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('keyboardShow' | 'keyboardHide')

```TypeScript
off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void
```

Disables listening for a keyboard visibility event. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 23

**Substitutes:** off(type: 'keyboardShow' | 'keyboardHide', callback?: () =&gt; void)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardShow' &#124; 'keyboardHide' | Yes | Event type.<br>- The value **'keyboardShow'** indicates the keyboard display event. <br>- The value **'keyboardHide'** indicates the keyboard hiding event. |
| callback | () =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('keyboardShow' | 'keyboardHide')

```TypeScript
off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void
```

Disables listening for a keyboard visibility event. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 23

**Substitutes:** off(type: 'keyboardShow' | 'keyboardHide', callback?: () =&gt; void)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardShow' &#124; 'keyboardHide' | Yes | Event type.<br>- The value **'keyboardShow'** indicates the keyboard display event. <br>- The value **'keyboardHide'** indicates the keyboard hiding event. |
| callback | () =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## on('inputStart')

```TypeScript
on(
      type: 'inputStart',
      callback: (kbController: KeyboardController, textInputClient: TextInputClient) => void
    ): void
```

Enables listening for the input method binding event. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 23

**Substitutes:** [on](arkts-ime-inputmethodengine-inputmethodability-i.md#oninputstart)(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) =&gt; void)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'inputStart' | Yes | Event type, which is **'inputStart'**. |
| callback | (kbController: KeyboardController, textInputClient: TextInputClient) =&gt; void | Yes | Callback used to return the **KeyboardController** and **TextInputClient** instances. |

## on('keyboardShow' | 'keyboardHide')

```TypeScript
on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void
```

Enables listening for a keyboard visibility event. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 23

**Substitutes:** on(type: 'keyboardShow' | 'keyboardHide', callback: () =&gt; void)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardShow' &#124; 'keyboardHide' | Yes | Event type.<br>- The value **'keyboardShow'** indicates the keyboard display event. <br>- The value **'keyboardHide'** indicates the keyboard hiding event. |
| callback | () =&gt; void | Yes | Callback used to return the result. |

## on('keyboardShow' | 'keyboardHide')

```TypeScript
on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void
```

Enables listening for a keyboard visibility event. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 23

**Substitutes:** on(type: 'keyboardShow' | 'keyboardHide', callback: () =&gt; void)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardShow' &#124; 'keyboardHide' | Yes | Event type.<br>- The value **'keyboardShow'** indicates the keyboard display event. <br>- The value **'keyboardHide'** indicates the keyboard hiding event. |
| callback | () =&gt; void | Yes | Callback used to return the result. |
