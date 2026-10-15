# SideBarContainerType

```TypeScript
declare enum SideBarContainerType
```

Enumerates the sidebar types of the container.

**Since:** 8

<!--Device-unnamed-declare enum SideBarContainerType--><!--Device-unnamed-declare enum SideBarContainerType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 2
```

When the component size is greater than or equal to [minSideBarWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#minsidebarwidth1) + [minContentWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#mincontentwidth), the Embed mode is used for display.

When the component size is smaller than [minSideBarWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#minsidebarwidth1) + [minContentWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#mincontentwidth), the Overlay mode is used for display. This mode applies to scenarios that require responsive layout or multi-device adaptation.

When [minSideBarWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#minsidebarwidth1) or [minContentWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#mincontentwidth) is not set, the default value of the unset API is used for calculation. If the calculated value is smaller than 600 vp, 600 vp is used as the threshold for mode switching.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerType-AUTO = 2--><!--Device-SideBarContainerType-AUTO = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISPLACE

```TypeScript
DISPLACE = 3
```

The sidebar and the content area are displayed in parallel, and the overflow part of the content area is moved outside the component. When the sidebar is expanded, the content area is displayed with a gray overlay (color: #33000000) and events are disabled. You can tap the content area to collapse the sidebar.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SideBarContainerType-DISPLACE = 3--><!--Device-SideBarContainerType-DISPLACE = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Embed

```TypeScript
Embed = 0
```

The sidebar is embedded in the component and displayed side by side with the content area. This mode applies to scenarios where both the sidebar and the content area need to be displayed.

When the overall container size remains unchanged, showing the sidebar shrinks the content area, and hiding the sidebar expands the content area.

When the component size is smaller than [minContentWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#mincontentwidth) + [minSideBarWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#minsidebarwidth1) and **showSideBar** is not set, the sidebar is not displayed by default.

When the **showSideBar** attribute is set, the value set by the **showSideBar** attribute prevails.

When [minSideBarWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#minsidebarwidth1) or [minContentWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#mincontentwidth) is not set, the default value of the corresponding API is used for calculation.

After the component is automatically hidden, if the sidebar is brought up by tapping the control button, the sidebar floats over the content area.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerType-Embed = 0--><!--Device-SideBarContainerType-Embed = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Overlay

```TypeScript
Overlay = 1
```

The sidebar floats over the content area and does not affect the size of the content area. This mode applies to scenarios where the sidebar needs to be displayed temporarily.

When the component size is smaller than [minContentWidth](arkts-arkui-sidebarcontainer-comp-attribute.md#mincontentwidth), the content area is displayed in a truncated manner.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerType-Overlay = 1--><!--Device-SideBarContainerType-Overlay = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
