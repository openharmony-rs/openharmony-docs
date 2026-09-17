# OnContentWillChangeCallback

```TypeScript
export type OnContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean
```

Defines the callback function triggered when the page content changes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| currentIndex | number | Yes | Index of the current tab. |
| comingIndex | number | Yes | Index of the tab to be switched to. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | - |
