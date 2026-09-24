# PopupV2Button

```TypeScript
export interface PopupV2Button
```

Defines the popup button

@typedef PopupV2Button

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { PopupV2, PopupV2InitInfo, PopupV2Button } from '@kit.ArkUI';
```

## action

```TypeScript
action?: Callback<void>
```

Set the button callback.

**Type:** Callback&lt;void&gt;

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonTextModifier

```TypeScript
buttonTextModifier?: TextModifier
```

The button text attributes of Popup.

**Type:** [TextModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: ResourceStr
```

Set the button display content.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
