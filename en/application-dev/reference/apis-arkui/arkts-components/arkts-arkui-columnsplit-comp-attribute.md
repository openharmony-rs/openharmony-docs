# ColumnSplit properties/events

```TypeScript
declare class ColumnSplitAttribute extends CommonMethod<ColumnSplitAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md#common), the following attributes are supported.

> **NOTE:** 
> 
> The default value of [shape clipping](arkts-arkui-common-comp-commonmethod-c.md#clip) of the **ColumnSplit** component is **true**.

The [universal events](arkts-arkui-common-comp.md#common) are supported.

**Inheritance/Implementation:** ColumnSplitAttribute extends CommonMethod<ColumnSplitAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## divider

```TypeScript
divider(value: ColumnSplitDividerStyle | null)
```

Sets the distance between the divider and the child components.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ColumnSplitDividerStyle](arkts-arkui-columnsplit-comp-columnsplitdividerstyle-i.md) &#124; null | Yes | Margin of the divider, which sets the distance between the divider and child components. The object properties include: **startMargin** (distance between the child component and the divider above) and **endMargin** (distance between the child component and the divider below).<br>Default value: **null**. When set to **null**, the distance between the divider and child components is 0 vp. <br>Illegal value: The default value is used. |

## resizeable

```TypeScript
resizeable(value: boolean)
```

Sets whether the divider can be dragged. When set to **true**, the user can drag the divider to adjust the height of adjacent child components. When set to **false**, the divider cannot be dragged and the child component height is fixed.

> **NOTE:** 
> 
> After initialization, when dynamic modification of the [margin](arkts-arkui-common-comp-commonmethod-c.md#margin),
> [border](arkts-arkui-common-comp-commonmethod-c.md#border), or [padding](arkts-arkui-common-comp-commonmethod-c.md#padding) universal attributes causes a child
> component size to exceed the spacing between adjacent dividers, dragging the divider to change the child
> component height is not supported.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the divider can be dragged. The value **true** means that the divider can be dragged, and **false** means the opposite. The height adjustment range of a child component is limited by its maximum and minimum heights. When the size of a child component is greater than the spacing between adjacent dividers, divider drag is not supported. After initialization, when dynamic modification of **margin**, **border**, or **padding** universal attributes causes the size of a child component to be greater than the spacing between adjacent dividers, divider drag to change the height of the child component is not supported.<br>Default value: **false** <br>Illegal value: The default value is used. |
