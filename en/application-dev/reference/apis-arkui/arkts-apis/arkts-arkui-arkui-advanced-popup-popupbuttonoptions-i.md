# PopupButtonOptions

```TypeScript
export interface PopupButtonOptions
```

Defines the button attributes and events.

**Since:** 11

<!--Device-unnamed-export interface PopupButtonOptions--><!--Device-unnamed-export interface PopupButtonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Popup, PopupButtonOptions, PopupIconOptions, PopupOptions, PopupTextOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

Click callback of the button.

By default, no operation is performed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupButtonOptions-action?: () => void--><!--Device-PopupButtonOptions-action?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Font color of the button text.

Default value: **$r('sys.color.ohos_id_color_text_primary_activated')**

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupButtonOptions-fontColor?: ResourceColor--><!--Device-PopupButtonOptions-fontColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

Font size of the button text.

Default value: **$r('sys.float.ohos_id_text_size_button2')**

Optional values of the string type: a string that can be converted to a number (for example, '10') or a string with a length unit (for example, '10px'). Setting a percentage string is not supported.

number: value range (0, +∞). When the type is number, the unit is fp.

The default value is used when an abnormal value is set.

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupButtonOptions-fontSize?: number | string | Resource--><!--Device-PopupButtonOptions-fontSize?: number | string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: ResourceStr
```

Text of the button.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupButtonOptions-text: ResourceStr--><!--Device-PopupButtonOptions-text: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
