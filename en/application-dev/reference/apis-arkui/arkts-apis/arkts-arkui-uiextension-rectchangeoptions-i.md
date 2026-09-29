# RectChangeOptions

```TypeScript
interface RectChangeOptions
```

Provides the values and reasons returned when the rectangle (position and size) of the component (**EmbeddedComponent** or **UIExtensionComponent**) changes.

**Since:** 14

<!--Device-uiExtension-interface RectChangeOptions--><!--Device-uiExtension-interface RectChangeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiExtension } from '@kit.ArkUI';
```

## reason

```TypeScript
reason: RectChangeReason
```

Reason for the rectangle change.

**Type:** [RectChangeReason](arkts-arkui-uiextension-rectchangereason-e.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 14.

<!--Device-RectChangeOptions-reason: RectChangeReason--><!--Device-RectChangeOptions-reason: RectChangeReason-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rect

```TypeScript
rect: window.Rect
```

New values of the rectangle of the component after the change.

**Type:** [window.Rect](arkts-arkui-window-rect-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 14.

<!--Device-RectChangeOptions-rect: window.Rect--><!--Device-RectChangeOptions-rect: window.Rect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
