# OnMenuItemClickWithTextCallback

```TypeScript
export type OnMenuItemClickWithTextCallback = (menuItem: TextMenuItem, value: string) => boolean
```

Invoke upon clicking an item, capable of intercepting the default system menu execution behavior.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| menuItem | [TextMenuItem](arkts-arkui-textmenuitem-i.md) | Yes | current clicked menu item. |
| value | string | Yes | selected text content. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Return true if the event is consumed; false otherwise. |
