# MenuItemGroup

The **MenuItemGroup** component represents a group of menu items. It supports setting the header and footer information of a group, and is used to organize and manage the classification structure of menu items. It is applicable to scenarios where multiple menu items need to be organized by category in a menu. By grouping, it clearly presents the hierarchical structure of the menu, improving the readability of the menu and the user experience.

> **NOTE:** 
> 
> - This component is supported since API version 9. Newly added APIs will be marked with a superscript to indicate their
> 
> - This component supports [WithTheme](arkts-arkui-withtheme-comp.md) since API version 26.0.0.

## Child Components

This component contains the [MenuItem](arkts-arkui-menuitem-comp.md) child component.

## Sample

For details, see [Example in Menu](../../../reference/apis-arkui/arkui-ts/ts-basic-components-menu.md#example).

## MenuItemGroup

```TypeScript
MenuItemGroup(value?: MenuItemGroupOptions)
```

Creates the MenuItemGroup component.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MenuItemGroupInterface-(value?: MenuItemGroupOptions): MenuItemGroupAttribute--><!--Device-MenuItemGroupInterface-(value?: MenuItemGroupOptions): MenuItemGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [MenuItemGroupOptions](arkts-arkui-menuitemgroup-comp-menuitemgroupoptions-i.md) | No | Header and footer of the menu item group.<br> If this parameter is not set, the header and footer information is not displayed. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [MenuItemGroupOptions](arkts-arkui-menuitemgroup-comp-menuitemgroupoptions-i.md) | Describes the header and footer information of the menu item group. |
