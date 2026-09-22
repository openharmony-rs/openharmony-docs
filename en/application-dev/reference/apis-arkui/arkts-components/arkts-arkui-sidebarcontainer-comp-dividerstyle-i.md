# DividerStyle

```TypeScript
interface DividerStyle
```

Sets the divider style.

> **NOTE:** 

> The settings of the universal size attributes **width** and **height** do not take effect for the
> sidebar child component.
> 
> The settings do not take effect for the sidebar content area either. By default, the sidebar content area takes
> up the remaining space of the sidebar container.

> If the [showSideBar](arkts-arkui-sidebarcontainer-comp-attribute.md#showsidebar) attribute is not set, the sidebar's visibility is
> subject to its size.

> - If the size is less than the sum of [minSideBarWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#minsidebarwidth) and [minContentWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#mincontentwidth), the sidebar is not displayed by default.
> 
> - If the size is greater than or equal to the sum of **minSideBarWidth** and **minContentWidth**, the sidebar is displayed by default.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Color of the divider.

Default value: **#000000, 3%**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: Length
```

Distance between the divider and the bottom of the sidebar.

Default value: **0**

Unit: vp

Value range: [0, +∞).

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: Length
```

Distance between the divider and the top of the sidebar.

Default value: **0**

Unit: vp

Value range: [0, +∞).

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth: Length
```

Stroke width of the divider.

Default value: **1vp**

Unit: vp

Value range: [0, +∞).

**NOTE:** 

Percentage values are not supported. The priority of this attribute is lower than that of the universal attribute [height](arkts-arkui-common-comp-commonmethod-c.md#height). If the value of this attribute is greater than that of **height**, cropping is performed based on the **height** settings. Due to hardware limitations on some devices where 1 px dividers may not display properly after rounding, you are advised to use the **2px** value.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 1vp

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
