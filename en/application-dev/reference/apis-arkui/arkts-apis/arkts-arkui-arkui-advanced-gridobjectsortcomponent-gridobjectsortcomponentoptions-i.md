# GridObjectSortComponentOptions

```TypeScript
export interface GridObjectSortComponentOptions
```

Provides configuration options for the **GridObjectSortComponent** component.

**Since:** 11

<!--Device-unnamed-export interface GridObjectSortComponentOptions--><!--Device-unnamed-export interface GridObjectSortComponentOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { GridObjectSortComponentType, GridObjectSortComponentItem, GridObjectSortComponentOptions, GridObjectSortComponent } from '@kit.ArkUI';
```

## addAreaTitle

```TypeScript
addAreaTitle?: ResourceStr
```

Second subtitle of the display area.

Default value: **Tap to add**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridObjectSortComponentOptions-addAreaTitle?: ResourceStr--><!--Device-GridObjectSortComponentOptions-addAreaTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## editTitle

```TypeScript
editTitle?: ResourceStr
```

Title displayed in the editing state.

Default value: **Edit**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridObjectSortComponentOptions-editTitle?: ResourceStr--><!--Device-GridObjectSortComponentOptions-editTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize?: number | Resource
```

Image size, in vp.

The value must be greater than or equal to 0.

Default value: **56vp**.

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridObjectSortComponentOptions-imageSize?: number | Resource--><!--Device-GridObjectSortComponentOptions-imageSize?: number | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## normalTitle

```TypeScript
normalTitle?: ResourceStr
```

Title displayed in the non-editing state.

Default value: **Channel**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridObjectSortComponentOptions-normalTitle?: ResourceStr--><!--Device-GridObjectSortComponentOptions-normalTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showAreaTitle

```TypeScript
showAreaTitle?: ResourceStr
```

First subtitle of the display area.

Default value: **Drag to sort**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridObjectSortComponentOptions-showAreaTitle?: ResourceStr--><!--Device-GridObjectSortComponentOptions-showAreaTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: GridObjectSortComponentType
```

Component display type: text only or image with text

Default value: **GridObjectSortComponentType.TEXT**

**Type:** [GridObjectSortComponentType](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponenttype-e.md)

**Default:** GridObjectSortComponentType.TEXT

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridObjectSortComponentOptions-type?: GridObjectSortComponentType--><!--Device-GridObjectSortComponentOptions-type?: GridObjectSortComponentType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
