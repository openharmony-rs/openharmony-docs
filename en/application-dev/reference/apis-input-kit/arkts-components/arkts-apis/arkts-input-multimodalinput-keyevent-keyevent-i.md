# KeyEvent

Key event.

@interface KeyEvent [since 9 - 11]

**Inheritance/Implementation:** KeyEvent extends [InputEvent](arkts-input-multimodalinput-inputevent-inputevent-i.md)

**Since:** 9

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

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core

## altKey

```TypeScript
altKey: boolean
```

Whether altKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core

## capsLock

```TypeScript
capsLock: boolean
```

Whether capsLock is enabled.

The value **true** indicates that capsLock is enabled, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core

## ctrlKey

```TypeScript
ctrlKey: boolean
```

Whether ctrlKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core

## fnKey

```TypeScript
fnKey: boolean
```

Whether fnKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core

## key

```TypeScript
key: Key
```

Defines a key.

**Type:** [Key](arkts-input-multimodalinput-keyevent-key-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core

## keys

```TypeScript
keys: Key[]
```

List of pressed keys.

**Type:** [Key](arkts-input-multimodalinput-keyevent-key-i.md)[]

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core

## logoKey

```TypeScript
logoKey: boolean
```

Whether logoKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core

## numLock

```TypeScript
numLock: boolean
```

Whether numLock is enabled.

The value **true** indicates that numLock is enabled, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core

## scrollLock

```TypeScript
scrollLock: boolean
```

Whether scrollLock is enabled.

The value **true** indicates that scrollLock is enabled, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core

## shiftKey

```TypeScript
shiftKey: boolean
```

Whether shiftKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core

## unicodeChar

```TypeScript
unicodeChar: number
```

Unicode character corresponding to the key.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.MultimodalInput.Input.Core
