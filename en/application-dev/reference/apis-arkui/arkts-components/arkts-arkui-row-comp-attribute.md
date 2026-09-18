# Row properties/events

In addition to the [universal attributes](arkts-arkui-commonmethod-c.md), the following attributes are supported.

The [universal events](arkts-arkui-commonmethod-c.md) are supported.

**Inheritance/Implementation:** RowAttribute extends CommonMethod<RowAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems(value: VerticalAlign)
```

Sets the alignment mode of child components in the vertical direction.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [VerticalAlign](../arkts-apis/arkts-arkui-verticalalign-e.md) | Yes | Alignment mode of child components in the vertical direction.<br>Default value: **VerticalAlign.Center** |

## justifyContent

```TypeScript
justifyContent(value: FlexAlign)
```

Sets the alignment mode of the child components in the horizontal direction.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FlexAlign](../arkts-apis/arkts-arkui-flexalign-e.md) | Yes | Alignment mode of child components in the horizontal direction.<br>Default value: **FlexAlign.Start** |

## reverse

```TypeScript
reverse(isReversed: Optional<boolean>)
```

Sets whether to reverse the horizontal arrangement of child components.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isReversed | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | Yes | Whether to reverse the horizontal arrangement of child components.<br> Default value: **true**. **true**: Child components are arranged in reverse order horizontally. **false**: Child components are arranged in normal order horizontally. |
