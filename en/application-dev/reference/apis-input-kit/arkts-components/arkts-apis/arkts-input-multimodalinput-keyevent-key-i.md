# Key

```TypeScript
export declare interface Key
```

Defines a key.

@interface Key [since 9 - 11]

**Since:** 9

<!--Device-unnamed-export declare interface Key--><!--Device-unnamed-export declare interface Key-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## Modules to Import

```TypeScript
import { Action, Key, KeyEvent } from '@kit.InputKit';
```

## code

```TypeScript
code: KeyCode
```

Key code.

**Type:** [KeyCode](arkts-input-multimodalinput-keycode-keycode-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Key-code: KeyCode--><!--Device-Key-code: KeyCode-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## deviceId

```TypeScript
deviceId: number
```

Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Key-deviceId: int--><!--Device-Key-deviceId: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## pressedTime

```TypeScript
pressedTime: number
```

Time when the key is pressed, in microseconds (μs) since the system starts.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Key-pressedTime: long--><!--Device-Key-pressedTime: long-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core
