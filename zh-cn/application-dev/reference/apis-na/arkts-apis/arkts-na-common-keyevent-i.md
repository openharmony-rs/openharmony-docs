# KeyEvent

KeyEvent object description:

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface KeyEvent--><!--Device-unnamed-export declare interface KeyEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stopPropagation

```TypeScript
stopPropagation(): void
```

Block event bubbling.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-stopPropagation(): void--><!--Device-KeyEvent-stopPropagation(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deviceId

```TypeScript
deviceId: int
```

Indicates the ID of the input device that triggers the current key.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-deviceId: int--><!--Device-KeyEvent-deviceId: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getModifierKeyState

```TypeScript
getModifierKeyState?: ModifierKeyStateGetter
```

Query the modifier key press state, support 'ctrl'|'alt'|'shift'

**类型：** [ModifierKeyStateGetter](arkts-na-modifierkeystategetter-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-getModifierKeyState?: ModifierKeyStateGetter--><!--Device-KeyEvent-getModifierKeyState?: ModifierKeyStateGetter-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## intentionCode

```TypeScript
intentionCode: IntentionCode
```

Intention code of a key or modifier keys.

**类型：** [IntentionCode](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-intentioncode-intentioncode-e.md)

**默认值：** IntentionCode.INTENTION_UNKNOWN

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-intentionCode: IntentionCode--><!--Device-KeyEvent-intentionCode: IntentionCode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isCapsLockOn

```TypeScript
isCapsLockOn?: boolean
```

Whether Caps Lock is on

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-isCapsLockOn?: boolean--><!--Device-KeyEvent-isCapsLockOn?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isNumLockOn

```TypeScript
isNumLockOn?: boolean
```

Whether Num Lock is on

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-isNumLockOn?: boolean--><!--Device-KeyEvent-isNumLockOn?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isScrollLockOn

```TypeScript
isScrollLockOn?: boolean
```

Whether Scroll Lock is on

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-isScrollLockOn?: boolean--><!--Device-KeyEvent-isScrollLockOn?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyCode

```TypeScript
keyCode: int
```

Key code of a key

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-keyCode: int--><!--Device-KeyEvent-keyCode: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keySource

```TypeScript
keySource: KeySource
```

Type of the input device that triggers the current key, such as the keyboard or handle.

**类型：** [KeySource](../../apis-arkui/arkts-apis/arkts-arkui-keysource-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-keySource: KeySource--><!--Device-KeyEvent-keySource: KeySource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyText

```TypeScript
keyText: string
```

Key value of a key.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-keyText: string--><!--Device-KeyEvent-keyText: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## metaKey

```TypeScript
metaKey: int
```

Indicates the status of the key when the key is pressed. The value 1 indicates the pressed state, and the value 0 indicates the unpressed state.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-metaKey: int--><!--Device-KeyEvent-metaKey: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: long
```

Timestamp when the key was pressed.

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-timestamp: long--><!--Device-KeyEvent-timestamp: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: KeyType
```

Type of a key.

**类型：** [KeyType](../../apis-arkui/arkts-apis/arkts-arkui-keytype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-type: KeyType--><!--Device-KeyEvent-type: KeyType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## unicode

```TypeScript
unicode?: long
```

Unicode of a key

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-unicode?: long--><!--Device-KeyEvent-unicode?: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

