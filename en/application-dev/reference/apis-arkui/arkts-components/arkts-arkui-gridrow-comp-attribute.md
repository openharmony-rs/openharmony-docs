# GridRow properties/events

In addition to the [universal events](arkts-arkui-commonmethod-c.md), the following events are supported.

**Inheritance/Implementation:** GridRowAttribute extends CommonMethod<GridRowAttribute>

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems(value: ItemAlign)
```

Sets the alignment mode of the **GridCol** components along the vertical main axis of the **GridRow** component. The alignment mode of the **GridCol** component can also be set using **alignSelf(ItemAlign)**. If both of the preceding methods are used, the setting of **alignSelf(ItemAlign)** prevails.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ItemAlign](../arkts-apis/arkts-arkui-itemalign-e.md) | Yes | Alignment mode of the **GridCol** components along the vertical main axis of the **GridRow** component.<br>Default value: **ItemAlign.Start**<br>Invalid values are treated as the default value.<br><br>**NOTE:** <br>**ItemAlign** supports the following enums: **ItemAlign.Start**, **ItemAlign.Center**, **ItemAlign.End**, and **ItemAlign.Stretch**. |

## onBreakpointChange

```TypeScript
onBreakpointChange(callback: (breakpoints: string) => void)
```

Triggered when the breakpoint changes.

> **NOTE:** 
> 
> 
> When [breakpointsreference](arkts-arkui-breakpointsreference-e.md) is set to **BreakpointsReference.ComponentSize**, you are not
> advised to dynamically change the padding or margin
> attribute value of the **GridRow** component in the **onBreakpointChange** callback.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (breakpoints: string) =&gt; void | Yes | Breakpoint change. The value can be **"xs"**, **"sm"**, **"md"**, **"lg"**, **"xl"**, or **"xxl"**. |
