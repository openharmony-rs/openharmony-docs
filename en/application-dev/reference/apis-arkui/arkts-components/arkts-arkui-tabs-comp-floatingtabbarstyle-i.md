# FloatingTabBarStyle

```TypeScript
interface FloatingTabBarStyle
```

Defines the floating style of the tab bar.

**Since:** 26.0.0

<!--Device-unnamed-interface FloatingTabBarStyle--><!--Device-unnamed-interface FloatingTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## adaptToHandedness

```TypeScript
adaptToHandedness?: boolean
```

Whether to follow the left-right layout of the operating hand.

The value **true** means to follow the left-right layout of the operating hand; the value **false** means not to follow the left-right layout of the operating hand.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-FloatingTabBarStyle-adaptToHandedness?: boolean--><!--Device-FloatingTabBarStyle-adaptToHandedness?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## barBottomMargin

```TypeScript
barBottomMargin?: Length
```

Distance from the tab bar to the bottom of the **Tabs**.

Value range: [0, +∞)

Default value: 28 vp.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-FloatingTabBarStyle-barBottomMargin?: Length--><!--Device-FloatingTabBarStyle-barBottomMargin?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## barSideMargin

```TypeScript
barSideMargin?: Length
```

Left and right margins in the default width calculation rule of the tab bar.

Value range: [0, +∞)

When the **Tabs** width is less than 600 vp, the default value is 16 vp. When the **Tabs** width is between 600 vp and 840 vp, the default value is 24 vp. When the **Tabs** width is greater than 840 vp, the default value is 32 vp.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-FloatingTabBarStyle-barSideMargin?: Length--><!--Device-FloatingTabBarStyle-barSideMargin?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## barWidth

```TypeScript
barWidth?: FloatingTabBarWidth
```

Width of the tab bar at different **Tabs** widths. For the default width calculation rule, see [FloatingTabBarWidth](arkts-arkui-tabs-comp-floatingtabbarwidth-i.md).

**Type:** [FloatingTabBarWidth](arkts-arkui-tabs-comp-floatingtabbarwidth-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-FloatingTabBarStyle-barWidth?: FloatingTabBarWidth--><!--Device-FloatingTabBarStyle-barWidth?: FloatingTabBarWidth-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: ResourceColor
```

Color of the mask. The mask display area is rendered with a transparency gradient based on the mask color, with the opacity decreasing from bottom to top. In light mode, the default value is **#CCF1F3F5**, displayed as white. In dark mode, the default value is **#99000000**, displayed as black.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-FloatingTabBarStyle-maskColor?: ResourceColor--><!--Device-FloatingTabBarStyle-maskColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskHeight

```TypeScript
maskHeight?: Length
```

Height of the mask. The upper edge of the mask display is 16 vp higher than the upper edge of the tab bar by default.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-FloatingTabBarStyle-maskHeight?: Length--><!--Device-FloatingTabBarStyle-maskHeight?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: UIMaterial.ImmersiveMaterial
```

Immersive material style of the tab bar backplate.

**Type:** [UIMaterial.ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-FloatingTabBarStyle-systemMaterial?: UIMaterial.ImmersiveMaterial--><!--Device-FloatingTabBarStyle-systemMaterial?: UIMaterial.ImmersiveMaterial-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
