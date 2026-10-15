# KeyPressedConfig

```TypeScript
interface KeyPressedConfig
```

Sets the key event consumption configuration.

**Since:** 16

<!--Device-inputConsumer-interface KeyPressedConfig--><!--Device-inputConsumer-interface KeyPressedConfig-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

## Modules to Import

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## action

```TypeScript
action: number
```

Subscription type.

**Note:**  Since API version 21, the value of this parameter can be **1** or **2**. The value **1** indicates subscription to only key press events, and the value **2** indicates subscription to both key press and release events.

In API version 20 or earlier versions, the value of this parameter can only be set to **1**, indicating subscription to only key press events.

**Type:** number

**Since:** 16

<!--Device-KeyPressedConfig-action: int--><!--Device-KeyPressedConfig-action: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

## isRepeat

```TypeScript
isRepeat: boolean
```

Whether to report repeated key events. The value **true** means to report repeated key events, and the value **false** means the opposite. The default value is **true**.

**Type:** boolean

**Since:** 16

<!--Device-KeyPressedConfig-isRepeat: boolean--><!--Device-KeyPressedConfig-isRepeat: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

## key

```TypeScript
key: number
```

Key value.

**Note:** Since API version 26.0.0, the [KEYCODE_FINGERPRINT_SLIDE_UP](arkts-input-multimodalinput-keycode-keycode-e.md) key and [KEYCODE_FINGERPRINT_SLIDE_DOWN](arkts-input-multimodalinput-keycode-keycode-e.md) key are newly supported. These are not universal key values across devices. Before using them, check whether the current device supports reporting the related key events. For details, see [Development Guide for Prioritized Response to System Function Keys](../../../device/input/keypressed-guidelines.md).

Since API version 21, the [KEYCODE_MEDIA_PLAY_PAUSE](arkts-input-multimodalinput-keycode-keycode-e.md) key, [KEYCODE_MEDIA_NEXT](arkts-input-multimodalinput-keycode-keycode-e.md) key, and [KEYCODE_MEDIA_PREVIOUS](arkts-input-multimodalinput-keycode-keycode-e.md) key are newly supported.

For API version 20 and earlier, only the [KEYCODE_VOLUME_UP](arkts-input-multimodalinput-keycode-keycode-e.md) key and [KEYCODE_VOLUME_DOWN](arkts-input-multimodalinput-keycode-keycode-e.md) key are supported.

**Type:** number

**Since:** 16

<!--Device-KeyPressedConfig-key: int--><!--Device-KeyPressedConfig-key: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer
