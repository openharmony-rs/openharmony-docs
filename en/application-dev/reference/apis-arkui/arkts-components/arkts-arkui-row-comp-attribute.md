# Row properties/events

```TypeScript
declare class RowAttribute extends CommonMethod<RowAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported.

The [universal events](arkts-arkui-common-comp-commonmethod-c.md) are supported.

**Inheritance/Implementation:** RowAttribute extends CommonMethod<RowAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems(value: VerticalAlign)
```

Sets the alignment format of child components in the vertical direction. After this attribute is set, child components are aligned in the specified manner in the vertical direction. By default, child components are vertically centered.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [VerticalAlign](../arkts-apis/arkts-arkui-verticalalign-e.md) | Yes | Alignment format of child components in the vertical direction.<br>Default value: **VerticalAlign.Center** |

## justifyContent

```TypeScript
justifyContent(value: FlexAlign)
```

Sets the alignment format of child components in the horizontal direction. After this attribute is set, child components are aligned in the specified manner in the horizontal direction. By default, child components are aligned at the start.

> **NOTE:** 
> 
> In a Row layout, if child components do not have [flexShrink](arkts-arkui-common-comp-commonmethod-c.md#flexshrink) set, they are not
> shrunk by default. That is, the sum of the main axis sizes of all child components may exceed the main axis of
> the container. In this case, the alignment behavior of **FlexAlign.Center** and **FlexAlign.End** changes, and
> the start position of child components is the same as that of **FlexAlign.Start**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FlexAlign](../arkts-apis/arkts-arkui-flexalign-e.md) | Yes | Alignment format of child components in the horizontal direction.<br>Default value: **FlexAlign.Start** <br>**Note:** Since API version 9, the **space** parameter does not take effect when **space** is a negative number or **justifyContent** is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**. |

## reverse

```TypeScript
reverse(isReversed: Optional<boolean>)
```

Sets whether to reverse the arrangement order of child components in the horizontal direction. When set to **true**, child components are arranged from right to left; when set to **false**, child components are arranged from left to right. This is applicable to scenarios where the display order of child components needs to be dynamically adjusted, such as internationalization layout adaptation.

> **NOTE:** 
> 
> If the **reverse** attribute is not set, the main axis direction is not reversed. If the **reverse** attribute
> is set and the parameter value is **undefined**, the default value **true** is used, and the main axis
> direction is reversed. If the parameter value is **false**, the main axis direction is not reversed. Since the
> main axis arrangement direction is affected by the universal attribute **direction**, if the **direction**
> attribute is set, when the **reverse** attribute is set to **true**, an additional reversal is always performed
> on the result of the direction attribute. If the **reverse** attribute is set to **false** or not set, the main
> axis direction is determined by the **direction** attribute without additional reversal.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isReversed | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the arrangement order of child components in the horizontal direction is reversed.<br>The value **true** means that the child components are arranged in reverse order in the horizontal direction (from right to left), and the value **false** means that the child components are arranged in normal order in the horizontal direction (from left to right). If the parameter value is **undefined**, it is treated as **true**, and the main axis direction is reversed. |
