# GridObjectSortComponent

```TypeScript
export declare struct GridObjectSortComponent
```

**GridObjectSortComponent** is a grid object organizer that you can use to edit, drag to sort, add, and delete grid objects.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **GridObjectSortComponent** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md#common)and [universal events](../arkts-components/arkts-arkui-common-comp.md#common) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **GridObjectSortComponent** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **GridObjectSortComponent** component.

**Since:** 11

**Decorator:** @Component

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel: () => void
```

Callback invoked when changes are canceled.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onSave

```TypeScript
onSave: (select: Array<GridObjectSortComponentItem>, unselect: Array<GridObjectSortComponentItem>) => void
```

Callback invoked when changes are saved. The data after the changes is returned.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

Data to pass. The maximum data length is 50 characters. If it is exceeded, only the first 50 characters are used.

**Type:** Array&lt;[GridObjectSortComponentItem](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentitem-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
