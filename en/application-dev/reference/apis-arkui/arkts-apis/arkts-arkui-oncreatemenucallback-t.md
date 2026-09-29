# OnCreateMenuCallback

```TypeScript
type OnCreateMenuCallback = (menuItems: Array<TextMenuItem>) => Array<TextMenuItem>
```

Triggered when the menu is created.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-type OnCreateMenuCallback = (menuItems: Array<TextMenuItem>) => Array<TextMenuItem>--><!--Device-unnamed-type OnCreateMenuCallback = (menuItems: Array<TextMenuItem>) => Array<TextMenuItem>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| menuItems | Array&lt;[TextMenuItem](arkts-arkui-textmenuitem-i.md)&gt; | Yes | Menu items currently displayed.<br>**NOTE:** <br>Modifications to the name, icon, and shortcut prompt of the default menu items do not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextMenuItem](arkts-arkui-textmenuitem-i.md)&gt; | Processed menu items. |
