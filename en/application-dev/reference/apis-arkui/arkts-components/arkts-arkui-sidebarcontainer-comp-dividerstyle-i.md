# DividerStyle

```TypeScript
interface DividerStyle
```

Sets the divider style.

> **NOTE:** 
> 
> When [width](arkts-arkui-common-comp-commonmethod-c.md#width1) and [height](arkts-arkui-common-comp-commonmethod-c.md#height1) are
> set for the sidebar child component, neither takes effect.
> 
> When [width](arkts-arkui-common-comp-commonmethod-c.md#width1) and [height](arkts-arkui-common-comp-commonmethod-c.md#height1) are
> set for the sidebar content area, neither takes effect. By default, the content area occupies the remaining space
> of the **SideBarContainer**.
> 
> When the [showSideBar](arkts-arkui-sidebarcontainer-comp-attribute.md#showsidebar) attribute is not set, the sidebar is displayed
> automatically based on the component size:
> 
> - Smaller than [minSideBarWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#minsidebarwidth1) +[minContentWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#mincontentwidth): the sidebar is not displayed by default.
> 
> - Greater than or equal to [minSideBarWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#minsidebarwidth1) +[minContentWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#mincontentwidth): the sidebar is displayed by default.

**Since:** 10

<!--Device-unnamed-interface DividerStyle--><!--Device-unnamed-interface DividerStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Color of the divider.

Default value: **#000000**, 3%, black.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DividerStyle-color?: ResourceColor--><!--Device-DividerStyle-color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: Length
```

Distance between the divider and the bottom of the sidebar.

Default value: **0**

Unit: vp

Value range: [0, +∞).

If the value is abnormal, the default value is used.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DividerStyle-endMargin?: Length--><!--Device-DividerStyle-endMargin?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: Length
```

Distance between the divider and the top of the sidebar.

Default value: **0**

Unit: vp

Value range: [0, +∞).

If the value is abnormal, the default value is used.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DividerStyle-startMargin?: Length--><!--Device-DividerStyle-startMargin?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth: Length
```

Width of the divider.

Default value: **1vp**

Unit: vp

Value range: [0, +∞)

The default value is used when an abnormal value is set.

**NOTE:** 

The width of the divider does not support percentage settings. It has a lower priority than the [common attribute height](arkts-arkui-common-comp-commonmethod-c.md#height1). If the width exceeds the size set by the common attribute, it is clipped according to the common attribute. On some devices, the divider may not be displayed due to 1-pixel rounding in hardware. 2 px is recommended.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 1vp

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DividerStyle-strokeWidth: Length--><!--Device-DividerStyle-strokeWidth: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
