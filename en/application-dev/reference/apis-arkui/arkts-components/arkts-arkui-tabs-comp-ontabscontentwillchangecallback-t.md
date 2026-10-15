# OnTabsContentWillChangeCallback

```TypeScript
declare type OnTabsContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean
```

Custom callback for intercepting **Tabs** page switching, triggered when a new page is about to be displayed.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnTabsContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean--><!--Device-unnamed-declare type OnTabsContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| currentIndex | number | Yes | Index of the currently displayed page. The index starts from 0. |
| comingIndex | number | Yes | Index of the new page to be displayed. The index starts from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | When the return value of the callback handler is **true**, **Tabs** can switch to the new page.<br>When the return value of the callback handler is **false**, **Tabs** cannot switch to the new page and still displays the original page content. |
