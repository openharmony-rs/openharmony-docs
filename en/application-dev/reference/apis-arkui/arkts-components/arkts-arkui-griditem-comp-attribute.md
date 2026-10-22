# GridItem properties/events

```TypeScript
declare class GridItemAttribute extends CommonMethod<GridItemAttribute>
```

Rules for setting **rowStart**, **rowEnd**, **columnStart**, and **columnEnd**: The valid value range of **rowStart** and **rowEnd** is 0 to the total number of rows minus 1. The valid value range of **columnStart** and **columnEnd** is 0 to the total number of columns minus 1. If **rowStart**, **rowEnd**, **columnStart**, or **columnEnd** is set, **GridItem** components occupy the specified number of rows (**rowEnd** - **rowStart** + 1) or columns (**columnEnd** - **columnStart** + 1). **GridItem** components with properly configured **rowStart** or **rowEnd** or **columnStart** or **columnEnd** attributes can only be laid out according to the specified grid coordinates when the parent **Grid** has both **columnsTemplate** and **rowsTemplate** defined. In the **Grid** component with both **columnsTemplate** and **rowsTemplate** set, **GridItem** components that have **rowStart** or **rowEnd** or **columnStart** or **columnEnd** set are laid out in a row-by-row then column-by-column manner. In the **Grid** component with only **columnsTemplate** set, **GridItem** components that have **columnStart** or **columnEnd** set are laid out in the specified columns. If there are already grid items in those columns, the grid items will be laid out in another row. In the **Grid** component with only **rowsTemplate** set, **GridItem** components that have **rowStart** or **rowEnd** set are laid out on the specified rows. If there are already grid items in those rows, the grid items will be laid out in another column. In the **Grid** component with neither **columnsTemplate** nor **rowsTemplate** set, the row and column number attributes have no effect for **GridItem** components. The following table describes the rules for handling abnormal values for **GridItem** row and column numbers.

| Attribute Setting | Exception Type| Layout Principles After Correction |  
| ----- |----| ------------------------ |  
| Only **columnsTemplate** is set | Any row or column exception| Laid out in a row-by-row then column-by-column manner|  
| Only **rowsTemplate** is set| Any row or column exception| Laid out in a row-by-row then column-by-column manner|  
| Both **rowsTemplate** and **columnsTemplate** are set| rowStart &lt; rowEnd | Row span = min(rowEnd - rowStart + 1, total number of rows)|  
| Both **rowsTemplate** and **columnsTemplate** are set| rowStart &gt; rowEnd | Laid out in a row-by-row then column-by-column manner|  
| Both **rowsTemplate** and **columnsTemplate** are set| columnStart &lt; columnEnd | Column span = min(columnEnd - columnStart + 1, total number of columns)|  
| Both **rowsTemplate** and **columnsTemplate** are set| columnStart &gt; columnEnd | Laid out in a row-by-row then column-by-column manner|

**Inheritance/Implementation:** GridItemAttribute extends CommonMethod&lt;GridItemAttribute&gt;

**Since:** 7

<!--Device-unnamed-declare class GridItemAttribute extends CommonMethod<GridItemAttribute>--><!--Device-unnamed-declare class GridItemAttribute extends CommonMethod<GridItemAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columnEnd

```TypeScript
columnEnd(value: number)
```

Sets the end column number of the component.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridItemAttribute-columnEnd(value: number): GridItemAttribute--><!--Device-GridItemAttribute-columnEnd(value: number): GridItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | End column number of the component. <br>In scenarios where you need to specify the start row and column numbers and the number of rows and columns of a **GridItem**, you are advised to use the [GridLayoutOptions](arkts-arkui-grid-comp-gridlayoutoptions-i.md) parameter of the **Grid** component. For details, see [Example 1: Creating a Fixed Row and Column Grid Layout](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). <br>Value range: [0, Total number of columns – 1]. |

## columnStart

```TypeScript
columnStart(value: number)
```

Sets the start column number of the component.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridItemAttribute-columnStart(value: number): GridItemAttribute--><!--Device-GridItemAttribute-columnStart(value: number): GridItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Start column number of the component. <br>In scenarios where you need to specify the start row and column numbers and the number of rows and columns of a **GridItem**, you are advised to use the [GridLayoutOptions](arkts-arkui-grid-comp-gridlayoutoptions-i.md) parameter of the **Grid** component. For details, see [Example 1: Creating a Fixed Row and Column Grid Layout](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). <br>Value range: [0, Total number of columns – 1]. |

## onSelect

```TypeScript
onSelect(event: (isSelected: boolean) => void)
```

Triggered when the selected state of the grid item changes.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridItemAttribute-onSelect(event: (isSelected: boolean) => void): GridItemAttribute--><!--Device-GridItemAttribute-onSelect(event: (isSelected: boolean) => void): GridItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (isSelected: boolean) =&gt; void | Yes | Callback invoked when the selected state changes. The input parameter **isSelected**: Whether the item is selected. The value **true** indicates that the item enters the mouse selection range and is selected, and **false** indicates that the item moves out of the mouse selection range and is not selected. |

## rowEnd

```TypeScript
rowEnd(value: number)
```

Sets the end row number of the component.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridItemAttribute-rowEnd(value: number): GridItemAttribute--><!--Device-GridItemAttribute-rowEnd(value: number): GridItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | End row number of the current element.<br>In scenarios where you need to specify the start row and column and the occupied rows and columns of a **GridItem**, you are advised to use the [GridLayoutOptions](arkts-arkui-grid-comp-gridlayoutoptions-i.md) parameter of **Grid**. For details, see [Example 1: Creating a Fixed Row and Column Grid Layout](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). <br>Value range: [0, Total Rows - 1] |

## rowStart

```TypeScript
rowStart(value: number)
```

Sets the start row number of the component.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridItemAttribute-rowStart(value: number): GridItemAttribute--><!--Device-GridItemAttribute-rowStart(value: number): GridItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Start row number of the component. <br>In scenarios where you need to specify the start row and column numbers and the number of rows and columns of a **GridItem**, you are advised to use the [GridLayoutOptions](arkts-arkui-grid-comp-gridlayoutoptions-i.md) parameter of the **Grid** component. For details, see [Example 1: Creating a Fixed Row and Column Grid Layout](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). <br>Value range: [0, Total number of rows – 1]. |

## selectable

```TypeScript
selectable(value: boolean)
```

Sets whether the grid item is selectable in the mouse selection box area. This attribute takes effect only when mouse box selection is enabled for the parent **Grid** container.

This attribute must be used before the [polymorphic style](arkts-arkui-common-comp.md) is set. Otherwise, the style settings will not take effect.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridItemAttribute-selectable(value: boolean): GridItemAttribute--><!--Device-GridItemAttribute-selectable(value: boolean): GridItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the grid item is selectable in the mouse selection box area. The value **true** means that the grid item is selectable in the mouse selection box area, and **false** means the opposite. <br>Default value: **true**. |

## selected

```TypeScript
selected(value: boolean)
```

Sets whether the grid item is selected. This attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

This attribute must be used before the [polymorphic style](arkts-arkui-common-comp.md) is set. Otherwise, the style settings will not take effect.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridItemAttribute-selected(value: boolean): GridItemAttribute--><!--Device-GridItemAttribute-selected(value: boolean): GridItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the current **GridItem** is selected. The value **true** indicates the selected state, and **false** indicates the unselected state.<br>Default value: **false** |

## forceRebuild

```TypeScript
forceRebuild(value: boolean)
```

Whether to re-create the component when it is being built.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. Whether to re-create the component
> is automatically determined based on the component attributes and child component changes. No manual
> configuration is required.

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-GridItemAttribute-forceRebuild(value: boolean): GridItemAttribute--><!--Device-GridItemAttribute-forceRebuild(value: boolean): GridItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to recreate this node when the component build is triggered. The value **true** means to recreate the node, and **false** means not to forcibly recreate the node.<br>Default value: **false** |
