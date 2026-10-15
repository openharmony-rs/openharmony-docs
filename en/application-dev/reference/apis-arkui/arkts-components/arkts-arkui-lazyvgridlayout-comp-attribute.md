# LazyVGridLayout properties/events

```TypeScript
declare class LazyVGridLayoutAttribute extends LazyGridLayoutAttribute<LazyVGridLayoutAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

**Inheritance/Implementation:** LazyVGridLayoutAttribute extends LazyGridLayoutAttribute&lt;LazyVGridLayoutAttribute&gt;

**Since:** 19

<!--Device-unnamed-declare class LazyVGridLayoutAttribute extends LazyGridLayoutAttribute<LazyVGridLayoutAttribute>--><!--Device-unnamed-declare class LazyVGridLayoutAttribute extends LazyGridLayoutAttribute<LazyVGridLayoutAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

<a id="columnstemplate1"></a>

## columnsTemplate

```TypeScript
columnsTemplate(value: string)
```

Sets the number of columns, fixed column width, or minimum column width of the grid. If this attribute is not set, one column will be used.

For example, **'1fr 1fr 2fr'** means that the parent component is divided into 3 columns, and the available width of the parent component is divided into 4 equal parts, with the first column occupying 1 part, the second column occupying 1 part, and the third column occupying 2 parts.

**columnsTemplate('repeat(auto-fit, track-size)')**: The layout automatically calculates the number of columns and their actual widths while respecting the minimum column width specified by **track-size**.

**columnsTemplate('repeat(auto-fill, track-size)')**: The layout automatically calculates the number of columns based on the fixed column width specified by **track-size**.

**columnsTemplate('repeat(auto-stretch, track-size)')** sets a fixed column width of **track-size**, uses columnsGap as the minimum column gap, and automatically calculates the number of columns and the actual column gap.

**repeat**, **auto-fit**, **auto-fill**, and **auto-stretch** are keywords. **track-size** indicates the column width, in units of px, vp, %, or any valid numeric value. The default unit is vp. **track-size** must include at least one valid column width.

The **auto-fit** and **auto-stretch** modes support only one valid column width value for **track-size**, and **track-size** in **auto-stretch** mode supports only px, vp, and valid numeric values, not %. The **auto-fill** mode supports one or more valid column widths, for example, **columnsTemplate('repeat(auto-fill, 20)')** and **columnsTemplate('repeat(auto-fill, 20 80px)')**.

For usage effects, see Example 3.

If this attribute is set to **'0fr'**, the column width is 0, and child components are not displayed. If this attribute is set to an invalid value, the child components are displayed in a fixed column.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-LazyVGridLayoutAttribute-columnsTemplate(value: string): LazyVGridLayoutAttribute--><!--Device-LazyVGridLayoutAttribute-columnsTemplate(value: string): LazyVGridLayoutAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Number of columns, fixed column width, or minimum column width value of the current grid layout. |

<a id="columnstemplate2"></a>

## columnsTemplate

```TypeScript
columnsTemplate(template: string | ItemFillPolicy)
```

Number of columns in the current grid layout. If this attribute is not set, one column will be used.

When template is of the string type, refer to [columnsTemplate(value: string)](#columnstemplate1) for the usage.

When template is of the **ItemFillPolicy** type, the number of columns is determined based on the [breakpoint type](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) corresponding to the width of the **LazyVGridLayout** component.

For example, the **ItemFillPolicy.BREAKPOINT_DEFAULT** component displays two columns when the component width falls within the sm or smaller breakpoint range, three columns for the md breakpoint range, and five columns for the lg or larger breakpoint range, with each column being 1 fr.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-LazyVGridLayoutAttribute-columnsTemplate(template: string | ItemFillPolicy): LazyVGridLayoutAttribute--><!--Device-LazyVGridLayoutAttribute-columnsTemplate(template: string | ItemFillPolicy): LazyVGridLayoutAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| template | string &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) | Yes | Number of columns in the current grid layout. |
