# RowSplit properties/events

```TypeScript
declare class RowSplitAttribute extends CommonMethod<RowSplitAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported.

> **NOTE:** 
> 
> The default value of [shape clipping](arkts-arkui-common-comp-commonmethod-c.md#clip) of the **RowSplit** component is
> **true**.

The [universal events](arkts-arkui-common-comp-commonmethod-c.md) are supported.

**Inheritance/Implementation:** RowSplitAttribute extends CommonMethod<RowSplitAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## resizeable

```TypeScript
resizeable(value: boolean)
```

Sets whether the divider is draggable. When set to **true**, the user can drag the divider to change the width of the child components; when set to **false**, the divider position is fixed.

> **NOTE:** 
> 
> After initialization, if the child component width is greater than the spacing between adjacent dividers due to
> an exception caused by dynamically modifying the universal attributes **margin**, **border**, and **padding**,
> dragging the divider to change the child component width is not supported.

> **NOTE:** 
> 
> The divider of **RowSplit** can change the width of the left and right child components, but only to the extent
> that the resultant width falls within the maximum and minimum widths of the child components. When the divider
> is dragged, the child component width is calculated in real time. When the minimum or maximum width set for the
> child component is reached, the divider stops moving.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the divider can be dragged. When set to **true**, the divider can be dragged; when set to **false**, the divider cannot be dragged.<br>Default value: **false** <br>Invalid value: handled as the default value. |
