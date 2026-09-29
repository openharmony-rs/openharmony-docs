# ListItemGroup properties/events

```TypeScript
declare class ListItemGroupAttribute extends CommonMethod<ListItemGroupAttribute>
```

In addition to the universal attributes, the following attributes are supported.

**Inheritance/Implementation:** ListItemGroupAttribute extends CommonMethod<ListItemGroupAttribute>

**Since:** 9

<!--Device-unnamed-declare class ListItemGroupAttribute extends CommonMethod<ListItemGroupAttribute>--><!--Device-unnamed-declare class ListItemGroupAttribute extends CommonMethod<ListItemGroupAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## childrenMainSize

```TypeScript
childrenMainSize(value: ChildrenMainSize)
```

Sets the size information of the child components of a **ListItemGroup** component along the main axis.

> **NOTE:** 
> 
> - When the child components of a **List** component include **ListItemGroup**, the **childrenMainSize** attribute must be set for both the **List** component and each **ListItemGroup** component. **ListItemGroup** provides the size information of its child components along the main axis through this attribute, so that the
> **childrenMainSize** attribute of the **List** component can take effect properly.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ListItemGroupAttribute-childrenMainSize(value: ChildrenMainSize): ListItemGroupAttribute--><!--Device-ListItemGroupAttribute-childrenMainSize(value: ChildrenMainSize): ListItemGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ChildrenMainSize](arkts-arkui-common-comp-childrenmainsize-c.md) | Yes | Size information of child components in the main axis direction. |

## divider

```TypeScript
divider(
    value: ListDividerOptions | null,
  )
```

Sets the style of the divider for the list items. By default, there is no divider.

**strokeWidth**, **startMargin**, and **endMargin** cannot be set in percentage.

When a list item has [polymorphic styles](arkts-arkui-common-comp.md) applied, the dividers above and below the pressed child component are not rendered.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListItemGroupAttribute-divider(    value: ListDividerOptions | null,  ): ListItemGroupAttribute--><!--Device-ListItemGroupAttribute-divider(    value: ListDividerOptions | null,  ): ListItemGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ListDividerOptions](arkts-arkui-list-comp-listdivideroptions-i.md) &#124; null | Yes | Style of the divider for the list items.<br> Default value: **null**<br>**Since:** 18 |
