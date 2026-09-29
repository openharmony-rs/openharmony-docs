# TabBarOptions

```TypeScript
declare interface TabBarOptions
```

Defines the options for configuring images and text content on the tabs.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

<!--Device-unnamed-declare interface TabBarOptions--><!--Device-unnamed-declare interface TabBarOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## badge

```TypeScript
badge?: TabBarBadgeStyle
```

Badge style of the tab. If this parameter is not set, no badge is displayed.

**Type:** [TabBarBadgeStyle](arkts-arkui-tabcontent-comp-tabbarbadgestyle-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-TabBarOptions-badge?: TabBarBadgeStyle--><!--Device-TabBarOptions-badge?: TabBarBadgeStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: string | Resource
```

Image for the tab. If this parameter is not set, no image is displayed.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabBarOptions-icon?: string | Resource--><!--Device-TabBarOptions-icon?: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: string | Resource
```

Text for the tab. If this parameter is not set, no text is displayed.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabBarOptions-text?: string | Resource--><!--Device-TabBarOptions-text?: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
