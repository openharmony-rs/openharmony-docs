# RowSplit properties/events

In addition to the [universal attributes](arkts-arkui-commonmethod-c.md), the following attributes are supported.

The [universal events](arkts-arkui-commonmethod-c.md) are supported.

**Inheritance/Implementation:** RowSplitAttribute extends CommonMethod<RowSplitAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## resizeable

```TypeScript
resizeable(value: boolean)
```

Sets whether the divider can be dragged.

> The divider of **RowSplit** can change the width of the left and right child components, but only to the
> extent that the resultant width falls within the maximum and minimum widths of the child components.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the divider can be dragged. **true**: The divider can be dragged. **false**: The divider cannot be dragged.<br>Default value: **false** <br>Invalid values are treated as the default value. |
