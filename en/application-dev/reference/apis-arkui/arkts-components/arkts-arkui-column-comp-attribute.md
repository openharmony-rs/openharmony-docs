# Column properties/events

```TypeScript
declare class ColumnAttribute extends CommonMethod<ColumnAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported.

The [universal events](arkts-arkui-common-comp-commonmethod-c.md) are supported.

**Inheritance/Implementation:** ColumnAttribute extends CommonMethod<ColumnAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems(value: HorizontalAlign)
```

Alignment mode of the child components in the horizontal direction.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [HorizontalAlign](../arkts-apis/arkts-arkui-horizontalalign-e.md) | Yes | Alignment format of the child components in the horizontal direction.<br>Default value: **HorizontalAlign.Center** |

## justifyContent

```TypeScript
justifyContent(value: FlexAlign)
```

Alignment mode of the child components in the vertical direction.

> **NOTE:** 
> 
> During the column layout, if [flexShrink](arkts-arkui-common-comp-commonmethod-c.md#flexshrink) is not set for a child component, the
> child component is not compressed by default. This can result in the total main axis size of all child components
> exceeding the container's main axis size, which makes **FlexAlign.Center** and **FlexAlign.End** ineffective.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FlexAlign](../arkts-apis/arkts-arkui-flexalign-e.md) | Yes | Alignment format of child components in the vertical direction. <br>Default value: **FlexAlign.Start** <br>**Note:** If the child component does not set [flexShrink](arkts-arkui-common-comp-commonmethod-c.md#flexshrink), **FlexAlign.Center** and **FlexAlign.End** may not take effect. For details, see the description below. When this parameter is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**, the [space](arkts-arkui-column-comp-columnoptions-i.md) attribute does not take effect. |

## reverse

```TypeScript
reverse(isReversed: Optional<boolean>)
```

Sets whether to reverse the vertical arrangement of child components.  
> **NOTE:** 
> 
> If the **reverse** attribute is not set, the main axis direction is not reversed. If the attribute is set and the
> parameter value is **undefined**, it defaults to **true**, and the main axis direction is reversed. The universal
> attribute **direction** only changes the cross axis direction of **Column**, not the main axis direction of
> **Column**, so it does not affect the **reverse** attribute.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isReversed | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the child components are arranged in reverse order in the vertical direction.<br>Default value: **true**. The value **true** indicates that the child components are arranged in reverse order in the vertical direction, and **false** indicates that they are arranged in normal order. |
