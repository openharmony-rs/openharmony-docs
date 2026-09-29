# KeyEvent

```TypeScript
export declare interface KeyEvent extends InputEvent
```

Key event.

@interface KeyEvent [since 9 - 11]

**Inheritance/Implementation:** KeyEvent extends [InputEvent](arkts-input-multimodalinput-inputevent-inputevent-i.md)

**Since:** 9

<!--Device-unnamed-export declare interface KeyEvent extends InputEvent--><!--Device-unnamed-export declare interface KeyEvent extends InputEvent-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## Modules to Import

```TypeScript
import { Action, Key, KeyEvent } from '@kit.InputKit';
```

## action

```TypeScript
action: Action
```

Key event type.

**Type:** [Action](arkts-input-multimodalinput-keyevent-action-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-action: Action--><!--Device-KeyEvent-action: Action-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## altKey

```TypeScript
altKey: boolean
```

Whether altKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-altKey: boolean--><!--Device-KeyEvent-altKey: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## capsLock

```TypeScript
capsLock: boolean
```

Whether capsLock is enabled.

The value **true** indicates that capsLock is enabled, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-capsLock: boolean--><!--Device-KeyEvent-capsLock: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## ctrlKey

```TypeScript
ctrlKey: boolean
```

Whether ctrlKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-ctrlKey: boolean--><!--Device-KeyEvent-ctrlKey: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## fnKey

```TypeScript
fnKey: boolean
```

Whether fnKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-fnKey: boolean--><!--Device-KeyEvent-fnKey: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## key

```TypeScript
key: Key
```

Defines a key.

**Type:** [Key](arkts-input-multimodalinput-keyevent-key-i.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-key: Key--><!--Device-KeyEvent-key: Key-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## keys

```TypeScript
keys: Key[]
```

List of pressed keys.

**Type:** [Key](arkts-input-multimodalinput-keyevent-key-i.md)[]

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-keys: Key[]--><!--Device-KeyEvent-keys: Key[]-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## logoKey

```TypeScript
logoKey: boolean
```

Whether logoKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-logoKey: boolean--><!--Device-KeyEvent-logoKey: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## numLock

```TypeScript
numLock: boolean
```

Whether numLock is enabled.

The value **true** indicates that numLock is enabled, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-numLock: boolean--><!--Device-KeyEvent-numLock: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## scrollLock

```TypeScript
scrollLock: boolean
```

Whether scrollLock is enabled.

The value **true** indicates that scrollLock is enabled, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-scrollLock: boolean--><!--Device-KeyEvent-scrollLock: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## shiftKey

```TypeScript
shiftKey: boolean
```

Whether shiftKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-shiftKey: boolean--><!--Device-KeyEvent-shiftKey: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## unicodeChar

```TypeScript
unicodeChar: number
```

Unicode character corresponding to the key.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-KeyEvent-unicodeChar: int--><!--Device-KeyEvent-unicodeChar: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core
