# TabViewCustomization

```TypeScript
interface TabViewCustomization
```

Defines the centralized customization configuration for the sidebar tab bar.

**Since:** 26.1.0

<!--Device-unnamed-interface TabViewCustomization--><!--Device-unnamed-interface TabViewCustomization-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## orderMap

```TypeScript
orderMap?: Map<number, number>
```

A map of TabContent index to the display priority of tab items in the sidebar.

**Type:** Map&lt;number, number&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-TabViewCustomization-orderMap?: Map<number, number>--><!--Device-TabViewCustomization-orderMap?: Map<number, number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sectionMap

```TypeScript
sectionMap?: Map<number, SidebarSection>
```

A map of TabContent index to sidebar section.

**Type:** Map&lt;number, [SidebarSection](arkts-arkui-tabcontent-comp-sidebarsection-i.md)&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-TabViewCustomization-sectionMap?: Map<number, SidebarSection>--><!--Device-TabViewCustomization-sectionMap?: Map<number, SidebarSection>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## visibilityMap

```TypeScript
visibilityMap?: Map<number, TabVisibility>
```

A map of TabContent index to sidebar visibility.

**Type:** Map&lt;number, [TabVisibility](arkts-arkui-tabcontent-comp-tabvisibility-e.md)&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-TabViewCustomization-visibilityMap?: Map<number, TabVisibility>--><!--Device-TabViewCustomization-visibilityMap?: Map<number, TabVisibility>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
