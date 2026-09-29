# MenuItem

The **MenuItem** component represents an item in a menu.

> **NOTE:** 
> 
> - This component is supported since API version 9. Newly added APIs will be marked with a superscript to indicate their
> 
> - This component supports [WithTheme](arkts-arkui-withtheme-comp.md) since API version 26.0.0.

## Child Components

Not supported

## MenuItem

```TypeScript
MenuItem(value?: MenuItemOptions | CustomBuilder)
```

Creates the MenuItem component.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MenuItemInterface-(value?: MenuItemOptions | CustomBuilder): MenuItemAttribute--><!--Device-MenuItemInterface-(value?: MenuItemOptions | CustomBuilder): MenuItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [MenuItemOptions](arkts-arkui-menuitem-comp-menuitemoptions-i.md) &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | No | Information about the menu item. Use the **MenuItemOptions** type when standard menu item configuration (such as the start icon, content, and label) is required; use the **CustomBuilder** type when the display content and layout of the menu item need to be customized. If this parameter is not passed, an empty **MenuItem** object is created. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [MenuItemOptions](arkts-arkui-menuitem-comp-menuitemoptions-i.md) | Provides information about the menu item. |
