# EditMenuOptions

```TypeScript
declare interface EditMenuOptions
```

EditMenuOptions

**Since:** 12

<!--Device-unnamed-declare interface EditMenuOptions--><!--Device-unnamed-declare interface EditMenuOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCreateMenu

```TypeScript
onCreateMenu(menuItems: Array<TextMenuItem>): Array<TextMenuItem>
```

Triggered when the menu is being created. Menu data can be configured within this callback. Both the input parameter and return value contain only level-1 menu items; level-2 menu items are not included.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EditMenuOptions-onCreateMenu(menuItems: Array<TextMenuItem>): Array<TextMenuItem>--><!--Device-EditMenuOptions-onCreateMenu(menuItems: Array<TextMenuItem>): Array<TextMenuItem>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| menuItems | Array&lt;[TextMenuItem](arkts-arkui-textmenuitem-i.md)&gt; | Yes | Menu items to be displayed.<br>**Note:** <br>Modifications to the name, icon, and shortcut key hint of the default menu items do not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextMenuItem](arkts-arkui-textmenuitem-i.md)&gt; | Processed menu items. |

## onMenuItemClick

```TypeScript
onMenuItemClick(menuItem: TextMenuItem, range: TextRange): boolean
```

Triggered when a menu item is tapped, used to handle the tap behavior of the menu item.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EditMenuOptions-onMenuItemClick(menuItem: TextMenuItem, range: TextRange): boolean--><!--Device-EditMenuOptions-onMenuItemClick(menuItem: TextMenuItem, range: TextRange): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| menuItem | [TextMenuItem](arkts-arkui-textmenuitem-i.md) | Yes | Menu item.<br>**Note:** <br>Since API version 23, for a first-level menu item that supports an expandable second-level menu, such as auto-fill, only the system default logic is executed, and user-defined logic is not executed. |
| range | [TextRange](arkts-arkui-textrange-i.md) | Yes | Selected text. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Execution logic of the menu item.<br>The value **true** indicates that the system default logic is intercepted and only the custom logic is executed. <br>The value **false** indicates that the custom logic is executed first, followed by the system logic. |

## onPrepareMenu

```TypeScript
onPrepareMenu?: OnPrepareMenuCallback
```

Triggered before the menu is displayed after the text selection area changes. You can set menu data in this callback.

Similar to [onCreateMenu](#oncreatemenu) but with a different trigger timing: onCreateMenu is triggered when the menu is created and is suitable for initializing menu items; this API is triggered after each selection area change and before the menu is displayed, and is suitable for dynamically adjusting the menu based on the selected content. Both can be used at the same time.

**Atomic service API:** This API supports use in atomic services since API version 20.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-EditMenuOptions-onPrepareMenu?: OnPrepareMenuCallback--><!--Device-EditMenuOptions-onPrepareMenu?: OnPrepareMenuCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
