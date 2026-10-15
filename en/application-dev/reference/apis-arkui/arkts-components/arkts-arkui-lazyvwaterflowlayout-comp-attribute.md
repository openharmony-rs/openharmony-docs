# LazyVWaterFlowLayout properties/events

```TypeScript
export declare class LazyVWaterFlowLayoutAttribute extends LazyWaterFlowLayoutAttribute<LazyVWaterFlowLayoutAttribute>
```

Defines the lazy vertical waterflow layout attribute.

**Inheritance/Implementation:** LazyVWaterFlowLayoutAttribute extends LazyWaterFlowLayoutAttribute&lt;LazyVWaterFlowLayoutAttribute&gt;

**Since:** 26.0.0

<!--Device-unnamed-export declare class LazyVWaterFlowLayoutAttribute extends LazyWaterFlowLayoutAttribute<LazyVWaterFlowLayoutAttribute>--><!--Device-unnamed-export declare class LazyVWaterFlowLayoutAttribute extends LazyWaterFlowLayoutAttribute<LazyVWaterFlowLayoutAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute, LazyWaterFlowLayoutAttribute } from '@kit.ArkUI';
```

## columnsTemplate

```TypeScript
columnsTemplate(value: string | ItemFillPolicy | undefined)
```

Sets the number of columns, fixed column width, or minimum column width of the current **LazyVWaterFlowLayout**. If this attribute is not set, one column is used by default.

- When **value** is of the string type, you can set the number of columns, fixed column width,  
or minimum column width of the current **LazyVWaterFlowLayout**. Typical values and their meanings are as follows. For usage effects, see [Example 3](#example-3-setting-adaptive-column-count):

    1. **columnsTemplate('1fr 1fr 2fr')** divides the **LazyVWaterFlowLayout** into three columns,
with the component width divided into four equal parts: the first column takes up one part, the second column takes up one part, and the third column takes up two parts.
    2. **columnsTemplate('repeat(auto-fit, track-size)')** sets the minimum column width to **track-size**
and automatically calculates the number of columns and the actual column width.
    3. **columnsTemplate('repeat(auto-fill, track-size)')** sets the fixed column width to **track-size**
and automatically calculates the number of columns.
    4. **columnsTemplate('repeat(auto-stretch, track-size)')** sets the fixed column width to **track-size**,
uses [columnsGap](#columnsgap) as the minimum column spacing, and automatically calculates the number of columns and the actual column spacing.

Here, **repeat**, **auto-fit**, **auto-fill**, and **auto-stretch** are keywords. **track-size** is the column width, which supports units including px, vp, %, or a valid number. The default unit is vp. **track-size** must include at least one valid column width. The **auto-fit** mode and **auto-stretch** mode support only one valid column width value for **track-size**, and in the **auto-stretch** mode, **track-size** supports only px, vp, and valid numbers, not %. The **auto-fill** mode supports one or more valid column widths, for example, **columnsTemplate('repeat(auto-fill, 20)')** and **columnsTemplate('repeat(auto-fill, 20 80px)')**.

- When **value** is of the **ItemFillPolicy** type, the number of columns is determined  
based on the [breakpoint type](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) corresponding to the width of the **LazyVWaterFlowLayout** component. For example, when the **fillType** attribute of **ItemFillPolicy** is set to **PresetFillType.BREAKPOINT_DEFAULT**, two columns are displayed when the component width falls within the sm or smaller breakpoint interval, three columns when within the md breakpoint interval, and five columns when within the lg or larger breakpoint interval, with each column set to **1fr** (meaning each column takes up one equal portion of the available width).

- When **value** is set to **undefined**, the default value (one column) is restored.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyVWaterFlowLayoutAttribute-columnsTemplate(value: string | ItemFillPolicy | undefined): LazyVWaterFlowLayoutAttribute--><!--Device-LazyVWaterFlowLayoutAttribute-columnsTemplate(value: string | ItemFillPolicy | undefined): LazyVWaterFlowLayoutAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) &#124; undefined | Yes | Number of columns, fixed column width, minimum column width value, or breakpoint fill policy of **LazyVWaterFlowLayout**. |
