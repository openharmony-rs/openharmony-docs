# OnMenuItemClickWithTextCallback

```TypeScript
export type OnMenuItemClickWithTextCallback = (menuItem: TextMenuItem, value: string) => boolean
```

Called when a menu item is tapped. It can intercept the execution of system default menu items (such as copy and paste menu items).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-export type OnMenuItemClickWithTextCallback = (menuItem: TextMenuItem, value: string) => boolean--><!--Device-unnamed-export type OnMenuItemClickWithTextCallback = (menuItem: TextMenuItem, value: string) => boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| menuItem | [TextMenuItem](../arkts-apis/arkts-arkui-textmenuitem-i.md) | Yes | Menu item that is currently clicked. |
| value | string | Yes | Selected text content. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Processing result of the menu item click event. The value true indicates that the event has been processed, and false indicates the opposite. |
