# Menu

The **Menu** component is a vertical list of items presented to the user.

> **NOTE** > > - This component is supported since API version 9. Newly added APIs will be marked with a superscript to indicate > their > > - The **Menu** component must be used together with the > [bindMenu](arkts-arkui-commonmethod-c.md#bindmenu) or > [bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu) > method. It does not work when used alone.

## Child Components

This component contains the MenuItem and MenuItemGroup child components.

## Menu

```TypeScript
Menu()
```

Creates a fixed container for a menu. This API does not have any parameters.

> **NOTE:** 
> 
> - Rules for calculating the width of menus and menu items:
> 
> 
> 
> - During the layout, the width of each menu item is expected to be the same. If a child component has its width set, the size calculation rule prevails.
> 
> 
> 
> - If no width is set for the **Menu** component, it applies a default two-column width to the **MenuItem**and **MenuItemGroup** child components. If a menu item's content area exceeds the two-column width, the
> **Menu** component automatically expands the menu item's content area.
> 
> 
> 
> - When an explicit width is set for the **Menu** component, its child components **MenuItem** and
> **MenuItemGroup** adopt a fixed width (equal to the **Menu** component's configured width minus the padding).
> 
> 
> 
> - The minimum width is 64 vp.
> 
> - Universal attributes unsupported by **Menu**: outline attributes and the shadow attribute

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Enums

| Name | Description |
| --- | --- |
| [SubMenuExpandingMode](arkts-arkui-submenuexpandingmode-e.md) | Enumerates the submenu expanding modes. |

## Examples

```TypeScript
### Example 1: Implementing a Multi-Level Menu

This example demonstrates how to implement a multi-level menu by configuring the builder parameter in MenuItem.


```

```TypeScript
### Example 2: Setting the Symbol Icon

This example demonstrates how to implement a menu with symbol icons by configuring symbolStartIcon and symbolEndIcon.


```

```TypeScript
### Example 3: Setting the Menu Submenu Expand Symbol

This example demonstrates how to use subMenuExpandSymbol to set the color and size of the menu submenu expand symbol.


```

```TypeScript
### Example 4: Using the Divider Style

This example demonstrates how to set the divider style using the menuItemDivider and menuItemGroupDivider attributes.


```

```TypeScript
### Example 5: Setting Multi-level Menus for a Custom Menu Item

This example demonstrates how to use subMenuBuilder to add multi-level menus for a custom menu item.

The [subMenuBuilder](ts-basic-components-menuitem.md#submenubuilder) attribute is added since API version 26.0.0.
```
