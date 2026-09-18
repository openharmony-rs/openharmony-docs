# GridItem properties/events

**Inheritance/Implementation:** GridItemAttribute extends CommonMethod<GridItemAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columnEnd

```TypeScript
columnEnd(value: number)
```

Sets the end column number of the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | End column number of the component.<br>In scenarios where you need to specify the start row and column numbers and the number of rows and columns of a **GridItem**, you are advised to use the [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) parameter of the **Grid** component. For details, see [Example 1: Creating a Fixed Row and Column Grid Layout](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). <br>Value range: [0, Total number of columns – 1]. |

## columnStart

```TypeScript
columnStart(value: number)
```

Sets the start column number of the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Start column number of the component.<br>In scenarios where you need to specify the start row and column numbers and the number of rows and columns of a **GridItem**, you are advised to use the [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) parameter of the **Grid** component. For details, see [Example 1: Creating a Fixed Row and Column Grid Layout](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). <br>Value range: [0, Total number of columns – 1]. |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Sets whether to re-create the component when it is being built.<br>Default value: **false**. |

## onSelect

```TypeScript
onSelect(event: (isSelected: boolean) => void)
```

Triggered when the selected state of the grid item changes.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (isSelected: boolean) =&gt; void | Yes | Callback invoked when the selected state changes. The input parameter **isSelected** returns **true** if the grid item is selected in the mouse selection box area; returns **false** otherwise. |

## rowEnd

```TypeScript
rowEnd(value: number)
```

Sets the end row number of the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | End row number of the component.<br>In scenarios where you need to specify the start row and column numbers and the number of rows and columns of a **GridItem**, you are advised to use the [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) parameter of the **Grid** component. For details, see [Example 1: Creating a Fixed Row and Column Grid Layout](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). <br>Value range: [0, Total number of rows – 1]. |

## rowStart

```TypeScript
rowStart(value: number)
```

Sets the start row number of the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Start row number of the component.<br>In scenarios where you need to specify the start row and column numbers and the number of rows and columns of a **GridItem**, you are advised to use the [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) parameter of the **Grid** component. For details, see [Example 1: Creating a Fixed Row and Column Grid Layout](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). <br>Value range: [0, Total number of rows – 1]. |

## selectable

```TypeScript
selectable(value: boolean)
```

Sets whether the grid item is selectable in the mouse selection box area. This attribute takes effect only when mouse box selection is enabled for the parent **Grid** container.

This attribute must be used before the polymorphic style is set. Otherwise, the style settings will not take effect.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the grid item is selectable in the mouse selection box area. The **value** means that the grid item is selectable in the mouse selection box area, and **false** means the opposite.<br>Default value: **true**. |

## selected

```TypeScript
selected(value: boolean)
```

Sets whether the grid item is selected. This attribute supports two-way binding through [&#36;&#36;](../../../ui/state-management/arkts-two-way-sync.md).

This attribute must be used before the polymorphic style is set. Otherwise, the style settings will not take effect.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the grid item is selected. The **value** means that the grid item is selected, and **false** means that the grid item is in the default state.<br>Default value: **false**. |
