# SideBarContainerType

Enumerates the types of sidebar containers.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Embed

```TypeScript
Embed = 0
```

The sidebar is embedded in the component and displayed side by side with the content area.

With the overall container size unchanged, displaying the sidebar reduces the content area, and hiding the sidebar expands the content area.

If the component size is less than the sum of [minContentWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#mincontentwidth) and [minSideBarWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#minsidebarwidth), and **showSideBar** is not set, the sidebar is automatically hidden.

If **minSideBarWidth** or **minContentWidth** is not set, the default value will be used for calculation.

The user can bring out the sidebar in Overlay mode by clicking the control button.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Overlay

```TypeScript
Overlay = 1
```

The sidebar is overlaid on top of the content area, without affecting the size of the content area.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 2
```

The sidebar is displayed in Embed mode when the component size is greater than or equal to the sum of **minSideBarWidth** and **minContentWidth**

and in Overlay mode otherwise.

If **minSideBarWidth** or **minContentWidth** is not set, the default value will be used for calculation. If the calculation result is less than 600 vp, 600 vp will be used as the breakpoint value for mode switching.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISPLACE

```TypeScript
DISPLACE = 3
```

The sideBar Displace. Sidebar is visible, content will offscreen to make space for sideBar.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
