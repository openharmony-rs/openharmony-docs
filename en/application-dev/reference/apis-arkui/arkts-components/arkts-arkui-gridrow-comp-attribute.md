# GridRow properties/events

```TypeScript
declare class GridRowAttribute extends CommonMethod<GridRowAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp-commonmethod-c.md), the following events are supported.

**Inheritance/Implementation:** GridRowAttribute extends CommonMethod<GridRowAttribute>

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems(value: ItemAlign)
```

Sets the alignment mode of **GridCol** within **GridRow** along the cross axis. The **GridCol** component can also set its own alignment mode through **alignSelf([ItemAlign](../arkts-apis/arkts-arkui-itemalign-e.md))**. When both alignment modes are set, the setting of the **GridCol** component takes precedence.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ItemAlign](../arkts-apis/arkts-arkui-itemalign-e.md) | Yes | Alignment mode of **GridCol** within **GridRow** along the cross axis.<br>Default value: **ItemAlign.Start** <br>Invalid value: The default value is used. <br>**NOTE:** <br>The supported **ItemAlign** values are: **ItemAlign.Start**, **ItemAlign.Center**, **ItemAlign.End**, **ItemAlign.Stretch**. |

## onBreakpointChange

```TypeScript
onBreakpointChange(callback: (breakpoints: string) => void)
```

Triggered when the breakpoint changes. The **breakpoints** parameter received by the callback indicates the current breakpoint value (with possible values of **"xs"**, **"sm"**, **"md"**, **"lg"**, **"xl"**, and **"xxl"**). You can perform corresponding UI layout adjustments or service logic processing based on the breakpoint value in the callback.

> **NOTE:** 
> 
> - When [breakpointsreference](arkts-arkui-gridrow-comp-breakpointsreference-e.md) is set to **BreakpointsReference.ComponentSize**, do not dynamically modify the [padding](arkts-arkui-common-comp-commonmethod-c.md#padding) or [margin](arkts-arkui-common-comp-commonmethod-c.md#margin) attribute of the **GridRow** component in the **onBreakpointChange** callback. Otherwise, it may cause cyclic triggering of component size calculation, layout jitter, or rendering performance degradation.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (breakpoints: string) =&gt; void | Yes | Callback invoked when the breakpoint changes. The parameter **breakpoints** indicates the current breakpoint value, which can be `"xs"`, `"sm"`, `"md"`, `"lg"`, `"xl"`, or `"xxl"`. |
