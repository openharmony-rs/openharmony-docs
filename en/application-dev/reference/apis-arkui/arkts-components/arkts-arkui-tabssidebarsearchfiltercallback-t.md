# TabsSidebarSearchFilterCallback

```TypeScript
declare type TabsSidebarSearchFilterCallback = (tabIndex: number, text: string) => boolean
```

Search filter callback.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tabIndex | number | Yes | Index of the tab to filter. |
| text | string | Yes | The current search text. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the tab matches the search criteria, **false** otherwise. |
