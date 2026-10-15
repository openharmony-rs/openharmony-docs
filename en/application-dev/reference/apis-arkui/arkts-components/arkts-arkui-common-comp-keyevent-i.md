# KeyEvent

```TypeScript
declare interface KeyEvent
```

KeyEvent object description.

**Since:** 7

<!--Device-unnamed-declare interface KeyEvent--><!--Device-unnamed-declare interface KeyEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getModifierKeyState

```TypeScript
getModifierKeyState?(keys: Array<string>): boolean
```

Obtains the pressed state of modifier keys. It is suitable for scenarios such as key combination judgment or shortcut key processing that require identifying whether modifier keys such as Ctrl, Alt, and Shift are pressed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-KeyEvent-getModifierKeyState?(keys: Array<string>): boolean--><!--Device-KeyEvent-getModifierKeyState?(keys: Array<string>): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | Yes | List of modifier keys. Supported modifier keys include 'Ctrl'&#124; 'Alt' &#124; 'Shift'. If an unsupported modifier key is passed in, error code 401 is thrown.<br>**NOTE:** <br>This API is not supported in stylus scenarios. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the modifier key is pressed. **true** if the modifier key is pressed; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. 2. Parameter verification failed. |

## stopPropagation

```TypeScript
stopPropagation: () => void
```

Blocks [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) propagation.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyEvent-stopPropagation: () => void--><!--Device-KeyEvent-stopPropagation: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## deviceId

```TypeScript
deviceId: number
```

ID of the input device that triggers the key event.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyEvent-deviceId: number--><!--Device-KeyEvent-deviceId: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## intentionCode

```TypeScript
intentionCode: IntentionCode
```

Intention corresponding to the key.

Default value: **IntentionCode.INTENTION_UNKNOWN**.

**Type:** [IntentionCode](arkts-arkui-common-comp-intentioncode-t.md)

**Default:** IntentionCode.INTENTION_UNKNOWN

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyEvent-intentionCode: IntentionCode--><!--Device-KeyEvent-intentionCode: IntentionCode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isCapsLockOn

```TypeScript
isCapsLockOn?: boolean
```

CapsLock state. **true**: locked. **false**: unlocked.

**Type:** boolean

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-KeyEvent-isCapsLockOn?: boolean--><!--Device-KeyEvent-isCapsLockOn?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isNumLockOn

```TypeScript
isNumLockOn?: boolean
```

NumLock state. **true**: locked. **false**: unlocked.

**Type:** boolean

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-KeyEvent-isNumLockOn?: boolean--><!--Device-KeyEvent-isNumLockOn?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isScrollLockOn

```TypeScript
isScrollLockOn?: boolean
```

ScrollLock state. **true**: locked. **false**: unlocked.

**Type:** boolean

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-KeyEvent-isScrollLockOn?: boolean--><!--Device-KeyEvent-isScrollLockOn?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## keyCode

```TypeScript
keyCode: number
```

Key value. For details about the key values provided by the key-based input devices, see [KeyCode](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keycode-keycode-e.md).

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyEvent-keyCode: number--><!--Device-KeyEvent-keyCode: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## keySource

```TypeScript
keySource: KeySource
```

Type of the input device that triggers the key event.

**Type:** [KeySource](../arkts-apis/arkts-arkui-keysource-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyEvent-keySource: KeySource--><!--Device-KeyEvent-keySource: KeySource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## keyText

```TypeScript
keyText: string
```

Name of the key.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyEvent-keyText: string--><!--Device-KeyEvent-keyText: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## metaKey

```TypeScript
metaKey: number
```

State of the Meta key (the key marked with a window logo, next to the **Ctrl** or **Alt** key at the lower-left corner of the keyboard) when the key event occurs. The value **1** indicates that the Meta key is pressed, and **0** indicates that it is not pressed.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyEvent-metaKey: number--><!--Device-KeyEvent-metaKey: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

Timestamp of the event. It is the interval between the time when the event is triggered and the time when the system starts, in nanoseconds.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyEvent-timestamp: number--><!--Device-KeyEvent-timestamp: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: KeyType
```

Key type.

**Type:** [KeyType](../arkts-apis/arkts-arkui-keytype-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyEvent-type: KeyType--><!--Device-KeyEvent-type: KeyType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## unicode

```TypeScript
unicode?: number
```

Unicode value of the key. Non-space basic Latin characters in the 0x0021-0x007E range are supported. Characters with a value of 0 are not supported. In the case of key combination, this API returns the Unicode value of the key corresponding to the key event.

**Type:** number

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-KeyEvent-unicode?: number--><!--Device-KeyEvent-unicode?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
