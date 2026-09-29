# ListItem properties/events

```TypeScript
declare class ListItemAttribute extends CommonMethod<ListItemAttribute>
```

In addition to the universal attributes, the following attributes are supported.

**Inheritance/Implementation:** ListItemAttribute extends CommonMethod<ListItemAttribute>

**Since:** 7

<!--Device-unnamed-declare class ListItemAttribute extends CommonMethod<ListItemAttribute>--><!--Device-unnamed-declare class ListItemAttribute extends CommonMethod<ListItemAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onSelect

```TypeScript
onSelect(event: (isSelected: boolean) => void)
```

Triggered when the selected state of the list item for multiselect changes.

This callback is triggered when the outer [List](arkts-arkui-list-comp.md) component has [multiSelectable](arkts-arkui-list-comp-attribute.md#multiselectable) set to **true** to enable mouse box selection, and the [selectable](#selectable) attribute of the current ListItem is set to **true**.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListItemAttribute-onSelect(event: (isSelected: boolean) => void): ListItemAttribute--><!--Device-ListItemAttribute-onSelect(event: (isSelected: boolean) => void): ListItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (isSelected: boolean) =&gt; void | Yes |  |

## selectable

```TypeScript
selectable(value: boolean)
```

Sets whether the current **ListItem** element can be selected by mouse frame selection. This takes effect only when the parent [List](arkts-arkui-list-comp.md) component has [multiSelectable](arkts-arkui-list-comp-attribute.md#multiselectable) set to **true** to enable mouse frame selection.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListItemAttribute-selectable(value: boolean): ListItemAttribute--><!--Device-ListItemAttribute-selectable(value: boolean): ListItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the **ListItem** element can be selected by mouse frame selection. When set to **true**, it can be selected by mouse frame selection; when set to **false**, it cannot.<br>Default value: **true**<br>**Note:** This takes effect only when the outer [List](arkts-arkui-list-comp.md) component sets [multiSelectable](arkts-arkui-list-comp-attribute.md#multiselectable) to **true** to enable mouse frame selection. |

## selected

```TypeScript
selected(value: boolean)
```

Sets whether the list item is selected. This attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md). This attribute must be used before the polymorphic style is set. Otherwise, the style settings will not take effect.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ListItemAttribute-selected(value: boolean): ListItemAttribute--><!--Device-ListItemAttribute-selected(value: boolean): ListItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the **ListItem** is selected. The value **true** means the selected state, and **false** means the default state.<br>Default value: **false**<br>**Note:** This attribute must be set before the polymorphic style is set for the selected state style to take effect. |

## swipeAction

```TypeScript
swipeAction(value: SwipeActionOptions)
```

Sets the swipe action item displayed when the list item is swiped out from the screen edge.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListItemAttribute-swipeAction(value: SwipeActionOptions): ListItemAttribute--><!--Device-ListItemAttribute-swipeAction(value: SwipeActionOptions): ListItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SwipeActionOptions](arkts-arkui-listitem-comp-swipeactionoptions-i.md) | Yes | Configuration of the swipe-out component of the **ListItem**, used to set the component displayed when swiped out, the swipe effect, and the swipe state callback. |

## editable

```TypeScript
editable(value: boolean | EditMode)
```

Sets whether to enable edit mode, where the list item can be deleted or moved.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. No substitute is provided.

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ListItemAttribute-editable(value: boolean | EditMode): ListItemAttribute--><!--Device-ListItemAttribute-editable(value: boolean | EditMode): ListItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean &#124; [EditMode](arkts-arkui-listitem-comp-editmode-e.md) | Yes | Whether the **ListItem** element is editable. When set to **true**, the list item enters the edit mode and can be deleted or moved. When set to **false**, the list item is not editable. When set to an **EditMode** enum value, **None** indicates that the edit operation is not restricted, **Deletable** indicates that the list item can be deleted, and **Movable** indicates that the list item can be moved.<br>Default value: **false** |

## sticky

```TypeScript
sticky(value: Sticky)
```

Sets the sticky effect of the list item.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** sticky

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ListItemAttribute-sticky(value: Sticky): ListItemAttribute--><!--Device-ListItemAttribute-sticky(value: Sticky): ListItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Sticky](arkts-arkui-listitem-comp-sticky-e.md) | Yes | Sticky effect of the list item.<br>Default value: **Sticky.None** |
