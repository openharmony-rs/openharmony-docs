# LazyVGridLayout properties/events

```TypeScript
declare class LazyVGridLayoutAttribute extends LazyGridLayoutAttribute<LazyVGridLayoutAttribute>
```

In addition to the universal attributes, the following attributes are supported.

In addition to the universal events, the following events are supported.

**Inheritance/Implementation:** LazyVGridLayoutAttribute extends LazyGridLayoutAttribute<LazyVGridLayoutAttribute>

**Since:** 19

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columnsTemplate

```TypeScript
columnsTemplate(value: string)
```

Sets the number of columns, fixed column width, or minimum column width of the grid. If this attribute is not set, one column will be used.

For example, **'1fr 1fr 2fr'** indicates three columns, with the first column taking up 1/4 of the parent component's full width, the second column 1/4, and the third column 2/4.

**columnsTemplate('repeat(auto-fit, track-size)')**: The layout automatically calculates the number of columns and their actual widths while respecting the minimum column width specified by **track-size**.

**columnsTemplate('repeat(auto-fill, track-size)')**: The layout automatically calculates the number of columns based on the fixed column width specified by **track-size**.

**columnsTemplate('repeat(auto-stretch, track-size)')**: The layout uses **columnsGap** to define the minimum gap between columns and automatically calculates the number of columns and the actual gap size based on the fixed column width specified by **track-size**.

**repeat**, **auto-fit**, **auto-fill**, and **auto-stretch** are keywords. **track-size** indicates the column width, in units of px, vp (default), %, or any valid numeric value. The value must be greater than or equal to a valid column width.

In auto-fit and auto-stretch modes, only a valid column width value is supported for **track-size**. Additionally, in auto-stretch mode, **track-size** only supports units such as px, vp, and valid numbers, but does not support percentage (%). The auto-fill mode supports one or more valid column widths, for example: columnsTemplate('repeat(auto-fill, 20)') or columnsTemplate('repeat(auto-fill, 20 80px)').

If this attribute is set to **'0fr'**, the column width is 0, and child components are not displayed. If this attribute is set to an invalid value, the child components are displayed in a fixed column.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Number of columns or minimum column width of the grid. |

<a id="columnstemplate-1"></a>

## columnsTemplate

```TypeScript
columnsTemplate(template: string | ItemFillPolicy)
```

Number of columns in the current grid layout. If this attribute is not set, one column will be used.

When template is of the string type, refer to [columnsTemplate(value: string)](#columnstemplate) for the usage.

When template is of the **ItemFillPolicy** type, the number of columns is determined based on the [breakpoint type](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) corresponding to the width of the **LazyVGridLayout** component.

For example, the **ItemFillPolicy.BREAKPOINT_DEFAULT** component displays two columns when the component width falls within the sm or smaller breakpoint range, three columns for the md breakpoint range, and five columns for the lg or larger breakpoint range, with each column being 1 fr.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| template | string &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) | Yes | Number of columns in the current grid layout. |
