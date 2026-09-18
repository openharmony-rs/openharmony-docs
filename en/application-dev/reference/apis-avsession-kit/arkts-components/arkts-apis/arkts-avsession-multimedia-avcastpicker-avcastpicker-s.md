# AVCastPicker

A picker view to show available streaming device list.

**Since:** 10

**Decorator:** @Component

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## Modules to Import

```TypeScript
import { AVCastPicker } from '@kit.AVSessionKit';
```

## onStateChange

```TypeScript
onStateChange?: (state: AVCastPickerState) => void
```

Picker state change callback.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [AVCastPickerState](arkts-avsession-multimedia-avcastpickerparam-avcastpickerstate-e.md) | Yes |  |

## activeColor

```TypeScript
activeColor?: Color | number | string
```

Assigns the color of picker component at active state.

**Type:** Color &#124; number &#124; string

**Since:** 11

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## colorMode

```TypeScript
colorMode?: AVCastPickerColorMode
```

Set the picker color mode.

**Type:** [AVCastPickerColorMode](arkts-avsession-multimedia-avcastpickerparam-avcastpickercolormode-e.md)

**Since:** 12

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## customPicker

```TypeScript
customPicker?: CustomBuilder
```

Set the custom builder for the picker appearance. If not set, system will show the default appearance for different device type.

**Type:** [CustomBuilder](../../apis-arkui/arkts-components/arkts-arkui-custombuilder-t.md)

**Since:** 12

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## normalColor

```TypeScript
normalColor?: Color | number | string
```

Assigns the color of picker component at normal state .

**Type:** Color &#124; number &#124; string

**Since:** 11

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## pickerStyle

```TypeScript
pickerStyle?: AVCastPickerStyle
```

Set the picker style.

**Type:** [AVCastPickerStyle](arkts-avsession-multimedia-avcastpickerparam-avcastpickerstyle-e.md)

**Since:** 12

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## sessionType

```TypeScript
sessionType?: string
```

Set the session type used by current picker component which can refer to AVSessionType in avSession. If not set, default value is 'audio'.

**Type:** string

**Since:** 12

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast
