# KeyPressedConfig

按键事件消费设置。

**起始版本：** 16

<!--Device-inputConsumer-interface KeyPressedConfig--><!--Device-inputConsumer-interface KeyPressedConfig-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

## 导入模块

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## action

```TypeScript
action: number
```

订阅指定的按键事件。

**说明：** 从API version 21开始，支持取值为1和2，取值为1表示订阅按键按下事件，取值为2表示同时订阅按键按下事件和按键抬起事件。

对于API version 20及之前的版本，仅支持取值为1，表示订阅按键按下事件。

**类型：** number

**起始版本：** 16

<!--Device-KeyPressedConfig-action: int--><!--Device-KeyPressedConfig-action: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

## isRepeat

```TypeScript
isRepeat: boolean
```

是否上报重复的按键事件。true表示上报，false表示不上报，默认值为true。

**类型：** boolean

**起始版本：** 16

<!--Device-KeyPressedConfig-isRepeat: boolean--><!--Device-KeyPressedConfig-isRepeat: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

## key

```TypeScript
key: number
```

按键键值。

**说明：** 从API version 26.0.0开始，新增支持[KEYCODE_FINGERPRINT_SLIDE_UP](arkts-input-multimodalinput-keycode-keycode-e.md)键和[KEYCODE_FINGERPRINT_SLIDE_DOWN](arkts-input-multimodalinput-keycode-keycode-e.md)键，非设备通用键值，使用前请判断当前设备是否支持相关按键事件上报，请参考[优先响应系统功能键开发指导](../../../../device/input/keypressed-guidelines.md)。

从API version 21开始，新增支持[KEYCODE_MEDIA_PLAY_PAUSE](arkts-input-multimodalinput-keycode-keycode-e.md)键、[KEYCODE_MEDIA_NEXT](arkts-input-multimodalinput-keycode-keycode-e.md)键和[KEYCODE_MEDIA_PREVIOUS](arkts-input-multimodalinput-keycode-keycode-e.md)键。

对于API version 20及之前的版本，仅支持[KEYCODE_VOLUME_UP](arkts-input-multimodalinput-keycode-keycode-e.md)键和[KEYCODE_VOLUME_DOWN](arkts-input-multimodalinput-keycode-keycode-e.md)键。

**类型：** number

**起始版本：** 16

<!--Device-KeyPressedConfig-key: int--><!--Device-KeyPressedConfig-key: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

