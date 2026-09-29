# PopupV2Button

```TypeScript
export interface PopupV2Button
```

Defines the related attributes and events of a button.

**Since:** 26.0.0

<!--Device-unnamed-export interface PopupV2Button--><!--Device-unnamed-export interface PopupV2Button-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { PopupV2, PopupV2InitInfo, PopupV2Button } from '@kit.ArkUI';
```

## action

```TypeScript
action?: Callback<void>
```

Callback for the button click event. No operation is performed by default.

**Type:** Callback&lt;void&gt;

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2Button-action?: Callback<void>--><!--Device-PopupV2Button-action?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonTextModifier

```TypeScript
buttonTextModifier?: TextModifier
```

Text properties of the button, such as the text color and font size.

Default value: **undefined**

When the value is **undefined**, the system button text properties are used by default.

**Model constraint**: This API can only be used in the stage model.

**Type:** [TextModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2Button-buttonTextModifier?: TextModifier--><!--Device-PopupV2Button-buttonTextModifier?: TextModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: ResourceStr
```

Button content.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2Button-text: ResourceStr--><!--Device-PopupV2Button-text: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
