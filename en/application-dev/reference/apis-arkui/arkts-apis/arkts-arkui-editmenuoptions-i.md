# EditMenuOptions

EditMenuOptions

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCreateMenu

```TypeScript
onCreateMenu(menuItems: Array<TextMenuItem>): Array<TextMenuItem>
```

Triggered when the menu is being created. Menu data can be configured within this callback. Both the input parameter and return value contain only level-1 menu items; level-2 menu items are not included.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| menuItems | Array&lt;[TextMenuItem](arkts-arkui-textmenuitem-i.md)&gt; | Yes | Menu items to be displayed.<br>**NOTE:** <br>Modifications to the name, icon, or shortcut hint of default menu items do not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextMenuItem](arkts-arkui-textmenuitem-i.md)&gt; | Menu items after the processing. |

## onMenuItemClick

```TypeScript
onMenuItemClick(menuItem: TextMenuItem, range: TextRange): boolean
```

Triggered when the specified menu item is clicked.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| menuItem | [TextMenuItem](arkts-arkui-textmenuitem-i.md) | Yes | Menu item.<br>**NOTE:** <br>Since API version 23, for level-1 menu items that support expandable level-2 menus (such as autofill), only the system default logic is executed and custom logic is not executed. |
| range | [TextRange](arkts-arkui-textrange-i.md) | Yes | Selected text. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Execution logic of the menu item.<br>Returns **true** if the default system logic is intercepted and only the custom logic is executed. <br>Returns **false** if the custom logic is executed before the default system logic. |

## onPrepareMenu

```TypeScript
onPrepareMenu?: OnPrepareMenuCallback
```

Callback invoked before the menu is displayed after the text selection area changes. Menu data can be configured within this callback.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
