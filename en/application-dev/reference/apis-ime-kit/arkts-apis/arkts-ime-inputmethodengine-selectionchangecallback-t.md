# SelectionChangeCallback

```TypeScript
export type SelectionChangeCallback = (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void
```

The callback of 'selectionChange' event.

**Since:** 26.1.0

<!--Device-inputMethodEngine-export type SelectionChangeCallback = (oldBegin: int, oldEnd: int, newBegin: int, newEnd: int) => void--><!--Device-inputMethodEngine-export type SelectionChangeCallback = (oldBegin: int, oldEnd: int, newBegin: int, newEnd: int) => void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| oldBegin | number | Yes | the old begin of the selected text. |
| oldEnd | number | Yes | the old end of the selected text. |
| newBegin | number | Yes | the new begin of the selected text. |
| newEnd | number | Yes | the new end of the selected text. |
