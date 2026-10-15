# FloatingTabBarWidth

```TypeScript
interface FloatingTabBarWidth
```

Defines the width of the tab bar under different **Tabs** widths.

> **NOTE:** 
> 
> - [barWidth](arkts-arkui-tabs-comp-attribute.md#barwidth) takes precedence over this API. When neither **barWidth** nor this API takes effect, the tab bar width uses the default calculation rule.
> 
> - The default calculation rule of the tab bar width is as follows. When the number of child nodes is 4, the maximum tab bar width is 328 vp. When the number of child nodes is greater than or equal to 5, the maximum tab bar width is 360 vp. When the **Tabs** width is greater than or equal to 1140 vp, the tab bar width and height are scaled up by 1.15 times.

**Since:** 26.0.0

<!--Device-unnamed-interface FloatingTabBarWidth--><!--Device-unnamed-interface FloatingTabBarWidth-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## largeBarWidth

```TypeScript
largeBarWidth?: Length
```

Width of the tab bar when the **Tabs** width is greater than 840 vp, or when the width is between 600 vp and 840 vp and the height-to-width ratio is greater than 0.8.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-FloatingTabBarWidth-largeBarWidth?: Length--><!--Device-FloatingTabBarWidth-largeBarWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mediumBarWidth

```TypeScript
mediumBarWidth?: Length
```

Width of the tab bar when the **Tabs** width is between 440 vp and 600 vp, or when the width is between 600 vp and 840 vp and the height-to-width ratio is less than 0.8.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-FloatingTabBarWidth-mediumBarWidth?: Length--><!--Device-FloatingTabBarWidth-mediumBarWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## smallBarWidth

```TypeScript
smallBarWidth?: Length
```

Width of the tab bar when the **Tabs** width is less than 440 vp.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-FloatingTabBarWidth-smallBarWidth?: Length--><!--Device-FloatingTabBarWidth-smallBarWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
