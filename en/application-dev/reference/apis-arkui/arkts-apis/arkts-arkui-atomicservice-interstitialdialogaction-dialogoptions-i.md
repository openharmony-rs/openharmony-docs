# DialogOptions

Defines the attributes specific to the dialog box and custom click actions for the user.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { InterstitialDialogAction, IconStyle, TitlePosition, BottomOffset } from '@kit.ArkUI';
```

## backgroundImage

```TypeScript
backgroundImage?: Resource
```

The background of the dialog.

**Type:** [Resource](arkts-arkui-resource-t.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## bottomOffsetType

```TypeScript
bottomOffsetType?: BottomOffset
```

The type of the bottom offset.

**Type:** [BottomOffset](arkts-arkui-atomicservice-interstitialdialogaction-bottomoffset-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## foregroundImage

```TypeScript
foregroundImage?: Resource
```

The foreground of the dialog.

**Type:** [Resource](arkts-arkui-resource-t.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconStyle

```TypeScript
iconStyle?: IconStyle
```

The style of the close button.

**Type:** [IconStyle](arkts-arkui-atomicservice-interstitialdialogaction-iconstyle-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDialogClick

```TypeScript
onDialogClick?: Callback<void>
```

The action after clicking dialog.

**Type:** Callback&lt;void&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDialogClose

```TypeScript
onDialogClose?: Callback<void>
```

The action after clicking close button.

**Type:** Callback&lt;void&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

The subtitle of the dialog.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subtitleColor

```TypeScript
subtitleColor?: ResourceStr | Color
```

The color of the subtitle.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md) &#124; [Color](arkts-arkui-color-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

The title of the dialog.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleColor

```TypeScript
titleColor?: ResourceStr | Color
```

The color of the title.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md) &#124; [Color](arkts-arkui-color-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titlePosition

```TypeScript
titlePosition?: TitlePosition
```

The relative position of the title and subtitle.

**Type:** [TitlePosition](arkts-arkui-atomicservice-interstitialdialogaction-titleposition-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## uiContext

```TypeScript
uiContext: UIContext
```

The UIContext required by the dialog.

**Type:** [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
