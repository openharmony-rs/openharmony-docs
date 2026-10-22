# GridObjectSortComponent

```TypeScript
export declare struct GridObjectSortComponent
```

Creates a GridObjectSortComponent component.

**Since:** 11

**Decorator:** @Component

<!--Device-unnamed-export declare struct GridObjectSortComponent--><!--Device-unnamed-export declare struct GridObjectSortComponent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { GridObjectSortComponentType, GridObjectSortComponentItem, GridObjectSortComponentOptions, GridObjectSortComponent } from '@kit.ArkUI';
```

## build

```TypeScript
build(): void
```

Build function of GridObjectSortComponent.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridObjectSortComponent-build(): void--><!--Device-GridObjectSortComponent-build(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel: () => void
```

Callback invoked when changes are canceled.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridObjectSortComponent-onCancel: () => void--><!--Device-GridObjectSortComponent-onCancel: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onSave

```TypeScript
onSave: (select: Array<GridObjectSortComponentItem>, unselect: Array<GridObjectSortComponentItem>) => void
```

Callback invoked when changes are saved. **select** indicates the selected data after editing, and **unselect** indicates the unselected data after editing.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridObjectSortComponent-onSave: (select: Array<GridObjectSortComponentItem>, unselect: Array<GridObjectSortComponentItem>) => void--><!--Device-GridObjectSortComponent-onSave: (select: Array<GridObjectSortComponentItem>, unselect: Array<GridObjectSortComponentItem>) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| select | Array&lt;[GridObjectSortComponentItem](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentitem-i.md)&gt; | Yes |  |
| unselect | Array&lt;[GridObjectSortComponentItem](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentitem-i.md)&gt; | Yes |  |

## dataList

```TypeScript
dataList: Array<GridObjectSortComponentItem>
```

Data to pass. The maximum number of data entries is 50. If the number of data entries exceeds 50, only the first 50 entries are used.

**Type:** Array&lt;[GridObjectSortComponentItem](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentitem-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridObjectSortComponent-dataList: Array<GridObjectSortComponentItem>--><!--Device-GridObjectSortComponent-dataList: Array<GridObjectSortComponentItem>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: GridObjectSortComponentOptions
```

Component configuration.

**Type:** [GridObjectSortComponentOptions](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentoptions-i.md)

**Since:** 11

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridObjectSortComponent-options: GridObjectSortComponentOptions--><!--Device-GridObjectSortComponent-options: GridObjectSortComponentOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
