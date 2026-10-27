# OnContextMenuUpdateCallback

```TypeScript
type OnContextMenuUpdateCallback = (menuItemId: WebContextMenuItemId, options?: WebContextMenuOptions) => void
```

Defines the callback type for context menu item status updates.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-type OnContextMenuUpdateCallback = (menuItemId: WebContextMenuItemId, options?: WebContextMenuOptions) => void--><!--Device-unnamed-type OnContextMenuUpdateCallback = (menuItemId: WebContextMenuItemId, options?: WebContextMenuOptions) => void-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| menuItemId | [WebContextMenuItemId](arkts-arkweb-web-comp-webcontextmenuitemid-e.md) | Yes | The ID of the context menu item. |
| options | [WebContextMenuOptions](arkts-arkweb-web-comp-webcontextmenuoptions-i.md) | No | The options of the context menu item. <br>Default value: See the default value of options. |
