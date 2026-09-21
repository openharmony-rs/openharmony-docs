# OnTabsContentWillChangeCallback

```TypeScript
declare type OnTabsContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean
```

Defines the callback invoked when a new page is about to be displayed.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| currentIndex | number | Yes | Index of the active tab. The index starts from 0. |
| comingIndex | number | Yes | Index of the new tab to be displayed. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The return value **true** means that the tab can switch to the new page.<br>The value **false** means that the tab cannot switch to the new page and will remain on the current page. |
