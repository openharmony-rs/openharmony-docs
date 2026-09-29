# MarkStyle

```TypeScript
declare interface MarkStyle
```

Define the style of checkbox mark.

**Since:** 10

<!--Device-unnamed-declare interface MarkStyle--><!--Device-unnamed-declare interface MarkStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Length
```

Size of the internal icon, in vp. The default size is the same as the width of the check box component.

Percentage values are not supported. If an invalid value is set, the default value is used.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MarkStyle-size?: Length--><!--Device-MarkStyle-size?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor?: ResourceColor
```

Color of the internal icon.

Default value: **Color.White**

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MarkStyle-strokeColor?: ResourceColor--><!--Device-MarkStyle-strokeColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

Thickness of the internal icon, in vp. Percentage values are not supported. If an invalid value is set, the default value is used.

Default value: **2**

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MarkStyle-strokeWidth?: Length--><!--Device-MarkStyle-strokeWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
