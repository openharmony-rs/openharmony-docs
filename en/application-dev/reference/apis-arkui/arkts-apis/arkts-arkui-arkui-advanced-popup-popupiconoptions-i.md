# PopupIconOptions

```TypeScript
export interface PopupIconOptions
```

Defines the icon options.

**Since:** 11

<!--Device-unnamed-export interface PopupIconOptions--><!--Device-unnamed-export interface PopupIconOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Popup, PopupButtonOptions, PopupIconOptions, PopupOptions, PopupTextOptions } from '@kit.ArkUI';
```

## borderRadius

```TypeScript
borderRadius?: Length | BorderRadiuses
```

Icon corner radius. Unit: vp.

Default value: `$r('sys.float.ohos_id_corner_radius_default_s')`

**Type:** [Length](arkts-arkui-length-t.md) &#124; [BorderRadiuses](arkts-arkui-borderradiuses-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupIconOptions-borderRadius?: Length | BorderRadiuses--><!--Device-PopupIconOptions-borderRadius?: Length | BorderRadiuses-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fillColor

```TypeScript
fillColor?: ResourceColor
```

Icon fill color. This property applies only to an SVG image.

By default, the icon color is not changed.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupIconOptions-fillColor?: ResourceColor--><!--Device-PopupIconOptions-fillColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

Icon height. Unit: vp.

Default value: **32vp**

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupIconOptions-height?: Dimension--><!--Device-PopupIconOptions-height?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## image

```TypeScript
image: ResourceStr
```

Icon content.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupIconOptions-image: ResourceStr--><!--Device-PopupIconOptions-image: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

Icon width. Unit: vp.

Default value: **32vp**

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupIconOptions-width?: Dimension--><!--Device-PopupIconOptions-width?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
