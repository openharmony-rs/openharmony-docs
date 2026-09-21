# ColumnSplitDividerStyle

```TypeScript
interface ColumnSplitDividerStyle
```

Sets the distance between the child component and the upper and lower dividers.

> **NOTE:** 
> 
> Similar to [RowSplit](arkts-arkui-rowsplit-comp-attribute.md#rowsplitattribute), the dividers of **ColumnSplit** adjust the height of adjacent child
> components. However, this adjustment is only applied to the extent that the resulting height stays within the
> height limits of the child components.
> 
> Universal attributes such as [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) and
> [margin](arkts-arkui-common-comp-commonmethod-c.md#margin) are supported. If **clip** is not set, the default value **true** is used.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: Dimension
```

Distance between the child component and the divider below it. This spacing can be adjusted (for example, to prevent content from overlapping with the divider or to improve layout aesthetics).

Default value: **0vp**

Value range: negative values are not supported.

Illegal value: treated as the default value, in which case the attribute value obtained by the [getInspectorByKey()](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-component-id.md#getinspectorbykey9) API is **undefined**.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 0

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: Dimension
```

Distance between the child component and the divider above it. This spacing can be adjusted (for example, to prevent content from overlapping with the divider or to improve layout aesthetics).

Default value: **0vp**

Value range: negative values are not supported.

Illegal value: treated as the default value, in which case the attribute value obtained by the [getInspectorByKey()](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-component-id.md#getinspectorbykey9) API is **undefined**.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 0

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
